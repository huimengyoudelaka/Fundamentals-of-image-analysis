

# ͼ�������������ҵ

����ʵ�������Sigmoid��Pow����Theta Schedule��[IR-SDE](https://github.com/Algolzw/image-restoration-sde)���иĽ���

 
## Ŀ¼

- [����ָ��](#����ָ��)
  - [��������](#��������)
  - [�ļ�Ŀ¼˵��](#�ļ�Ŀ¼˵��)
  - [���ݼ�����](#���ݼ�����)
  - [��������](#��������)
  - [ģ��ѵ��](#ģ��ѵ��)
  - [ģ�Ͳ���](#ģ�Ͳ���)
  - [ģ������](#ģ������)

## ����ָ��

### ��������

1. cuda: 9.1
2. python 3.7
3. pytorch 1.7

### �ļ�Ŀ¼˵��

```
IR-SDE
��  README.md
��  
����codes
��  ����config
��  ��  ����denoising-sde
��  ��      ��  inference.py
��  ��      ��  options.py
��  ��      ��  test.py
��  ��      ��  test.sh #���Խű�
��  ��      ��  train.py
��  ��      ��  train.sh #ѵ���ű�
��  ��      ��  
��  ��      ����models
��  ��      ��  ��  base_model.py
��  ��      ��  ��  denoising_model.py
��  ��      ��  ��  lr_scheduler.py
��  ��      ��  ��  networks.py
��  ��      ��  ��  optimizer.py
��  ��      ��  ��  __init__.py
��  ��      ��  ��  
��  ��      ��  ����modules
��  ��      ��          DenoisingNAFNet_arch.py
��  ��      ��          DenoisingUNet_arch.py
��  ��      ��          loss.py
��  ��      ��          module_util.py
��  ��      ��          __init__.py
��  ��      ��          
��  ��      ����options
��  ��          ����test
��  ��          ��      ir-sde.yml #��������
��  ��          ��      
��  ��          ����train
��  ��                  ir-sde.yml #ѵ������
��  ��                  
��  ����data
��  ��      BokehLQGT_dataset.py
��  ��      BokehLQ_dataset.py
��  ��      data_sampler.py
��  ��      GT_dataset.py
��  ��      LQGT_dataset.py
��  ��      LQ_dataset.py
��  ��      StereoLQGT_dataset.py
��  ��      StereoLQ_dataset.py
��  ��      util.py
��  ��      __init__.py
��  ��      
��  ����utils
��          deg_utils.py
��          file_utils.py
��          img_utils.py
��          sde_utils.py
��          __init__.py
��          
����dataset #���ݼ�
����experiments #ģ�ͱ���
����results #ʵ����


```
### ���ݼ�����
ѵ������DIV2K��Flickr2K��BSD500�Լ�Waterloo Explore�ĸ����ݼ��вɼ��ĸ�����ͼ��������ϵõ���ͼ��ŵ�ͬһ�ļ����¼��ɣ�,ѵ����ɵ�ģ����McMaster��Kodak24�Լ�CBSD68�������ݼ��Ͻ��в���,��7�����ݼ��ɴ�[SWinIR](https://github.com/JingyunLiang/SwinIR#training)���ء�
### ��������
 - ѵ����������./codes/config/denoising-sde/options/train/ir-sde.yml�����޸ġ�

 - ���Բ�������./codes/config/denoising-sde/options/test/ir-sde.yml�����޸ġ�

 - sdeѵ���Ͳ��ԵĲ�������schedule��Ӧ����һ�¡�
### ģ��ѵ��

ֱ������train.sh�ű����ɿ�ʼѵ����ѧϰ�ʡ�gpu�Լ�ѵ������������[��������](#��������)���޸ġ�

ѵ���ű�
 - �࿨����ѵ��

```
python -m torch.distributed.launch --nproc_per_node=2 --master_port 66666  train.py -opt './options/train/ir-sde.yml' --launcher pytorch
```
 - ����ѵ��
```
python train.py -opt './options/train/ir-sde.yml'
```
### ģ�Ͳ���
ֱ������test.sh�ű����ɿ�ʼ���ԣ����Լ���������[��������](#��������)���޸ġ�

���Խű�
```
python test.py -opt './options/test/ir-sde.yml'
```
### ģ������
ѵ���õ�ģ�Ϳ�ͨ��[�ȸ�����](https://drive.google.com/drive/folders/1ly96E24_w-2C5z6BxSSVgNyh7QUNK5sG?usp=sharing)���ء�
