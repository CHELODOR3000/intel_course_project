<h1 align="center">Multimodal Emotion Recognition with OpenVINO™</h1>
<h2 align="center">Model convertations</h2>
<h4>To convert PyTorch model to ONNX format, use the code below:</h4>
<br>
```bash
# Path to your model
PATH = r'models\enet_b0_8\enet_b0_8.pt'

# Load model and set the model in evaluation mode
feature_extractor_model = torch.load(PATH)
feature_extractor_model.eval()

# Create dummy input for the model. It will be used to run the model inside export function.
dummy_input = torch.randn(1, 3, 224, 224).cuda()
# Call the export function
torch.onnx.export(feature_extractor_model, (dummy_input, ), 'enet_b0_8.onnx')
```
#### To convert ONNX model to IR format in cmd use a command like:
```bash
mo --input_model your_ONNX_model -o output_directory_for_IR_model --data_type FP32_or_FP16_or_FP8
```
#### In our case we used the following commands:
FP32:
```bash
mo --input_model D:\Users\amira\openvino_env\Lib\site-packages\openvino\model_zoo\models\group_project\enet_b0_8\enet_b0_8.onnx -o D:\Users\amira\openvino_env\Lib\site-packages\openvino\model_zoo\models\group_project\enet_b0_8 --data_type FP32
```
FP16:
```bash
mo --input_model D:\Users\amira\openvino_env\Lib\site-packages\openvino\model_zoo\models\group_project\enet_b0_8\enet_b0_8.onnx -o D:\Users\amira\openvino_env\Lib\site-packages\openvino\model_zoo\models\group_project\enet_b0_8 --data_type FP16
```
