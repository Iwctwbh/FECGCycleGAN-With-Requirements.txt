适用版本：python 3.6 - 3.8

安装包 Install required Python packages
```bash
pip install scipy, scikit-learn, pyedflib, padasip, matplotlib, tensorflow==2.5, keras==2.4
pip install git+https://www.github.com/keras-team/keras-contrib.git
```
如果使用的gpu版本，需要安装cuda和cudnn。 If using the GPU version, install cuda and cudnn.
```bash
conda install -c anaconda cudnn
```
在安装好的keras中的generic_utils.py文件结尾添加以下代码。 Add the following code to the end of generic_utils.py in the installed Keras directory.
(Lib\site-packages\keras\utils\generic_utils.py)
```python
def populate_dict_with_module_objects(target_dict, modules, obj_filter):
  for module in modules:
    for name in dir(module):
      obj = getattr(module, name)
      if obj_filter(obj):
        target_dict[name] = obj

def to_snake_case(s):
    return ''.join(['_' + ch.lower() if ch.isupper() else ch for ch in str(s)]).lstrip('_')
```
For training the model use code in test.test_CycleGAN 

![alt text](https://github.com/antecessor/FECGCycleGAN/blob/master/4_60.png)


Top left: MECG <br>
Top middle: extracted FECG before SG filter<br>
Bottom left: Original scalp FECG<br>
Bottom middle: generated MECG without any postprocessing<br>


## Reference:
Mohebian, M.R., shahim Vedaei, S., Wahid, K.A., Dinh, A., Marateb, H.R. and Tavakolian, K., 2021. Fetal ECG Extraction from Maternal ECG using Attention-based CycleGAN. IEEE Journal of Biomedical and Health Informatics.
