# Adaptive Token Dictionary

Ветка для запуска (без результатов). Результаты находится на ветке results.


### Установка
```bash
git clone https://github.com/LabShuHangGU/Adaptive-Token-Dictionary.git
conda create -n ATD python=3.9
conda activate ATD
Перейти в папку с проектом
pip install -r requirements.txt
pip install six
python setup.py develop - обязательно использовать каждый раз при смене окружения
```
После этого:

- Скачать тестировочный датасет https://drive.google.com/file/d/1_FvS_bnSZvJWx9q4fNZTR8aS15Rb0Kc6/view?usp=sharing (если необходимо тестирование/обучение) и поместить в ./datasets
- Скачать модели отсюда https://drive.google.com/drive/folders/1D3BvTS1xBcaU1mp50k3pBzUWb7qjRvmB?usp=sharing и поместить их в ./experiments/pretrained_models


## Запуск на своих изображениях
```bash
# Для классического SR (первая строчка - для одного изображения, вторая - для папки)
python inference.py -i test_image.png -o results/test/ --scale 4 --task classical
python inference.py -i test_images/ -o results/test/ --scale 4 --task classical


# Легковесные модели
python inference.py -i test_image.png -o results/test/ --scale 4 --task lightweight
python inference.py -i test_images/ -o results/test/ --scale 4 --task lightweight

```
Параметр scale можно принимать значения: 2, 3, 4.  
Параметр -i обозначает input, может быть путем до каталога/фотографии;
Параметр -o обозначает каталог для сохранения результата.

## Тестирование модели
Запустить одну (или все) команды ниже:
```bash
python basicsr/test.py -opt options/test/001_ATD_SRx2_finetune.yml
python basicsr/test.py -opt options/test/002_ATD_SRx3_finetune.yml
python basicsr/test.py -opt options/test/003_ATD_SRx4_finetune.yml
python basicsr/test.py -opt options/test/101_ATD_light_SRx2_scratch.yml
python basicsr/test.py -opt options/test/102_ATD_light_SRx3_finetune.yml
python basicsr/test.py -opt options/test/103_ATD_light_SRx4_finetune.yml
```

## Acknowledgements
This code is built on [BasicSR](https://github.com/XPixelGroup/BasicSR).

