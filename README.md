<!DOCTYPE html>
<html lang="en">
<head>


<h1>Colon Tumor Detection using YOLOv11 Instance Segmentation</h1>

<h2>Project Overview</h2>
<p>This project detects and segments tumors (polyps) in colonoscopy videos using the YOLOv11 instance segmentation model. It uses deep learning to provide real-time tumor detection and mask segmentation from colonoscopy footage, supporting early and accurate diagnosis of colorectal cancer.</p>

<h2>Features</h2>
<ul>
  <li>Instance segmentation of tumors in colonoscopy video frames</li>
  <li>Custom training on a manually annotated dataset labeled as <strong>tumor</strong></li>
  <li>Outputs bounding boxes and segmentation masks on detected tumors</li>
  <li>Saves output videos with tumor annotations</li>
</ul>

<h2>Technologies Used</h2>
<ul>
  <li>Python</li>
  <li>PyTorch</li>
  <li>Ultralytics YOLOv11</li>
  <li>OpenCV</li>
  <li>Roboflow (for dataset annotation)</li>
</ul>

<h2>Dataset</h2>
<ul>
  <li>Total of <strong>585 colonoscopy images</strong> annotated with segmentation masks using Roboflow</li>
  <li>The single class label used is <strong>tumor</strong></li>
  <li><strong>527 images</strong> used for training; rest for validation/testing</li>
</ul>

<h2>Installation</h2>
<pre><code>git clone https://github.com/anandakumar15/Colon-Polyps.git
cd colonpolyps

python -m venv venv
source venv/bin/activate      # On Windows: venv\Scripts\activate

pip install ultralytics opencv-python torch numpy
</code></pre>

<h2>Usage</h2>

<h3>Important</h3>
<p>Before running any scripts, <strong>update and configure dataset and model paths</strong> in these files to avoid errors:</p>
<ul>
  <li><code>data.yaml</code> — Set correct paths to training and validation image folders and labels. The class name must be <code>"tumor"</code>.</li>
  <li><code>modeltrain.py</code> — Set dataset config file path and (if needed) pretrained weights path.</li>
  <li><code>detect.py</code> — Update paths to <code>colonoscopy.mp4</code> and <code>best.pt</code>.</li>
</ul>

<h3>Training the Model</h3>
<pre><code>python modeltrain.py
</code></pre>
<p><strong>Note:</strong> The <code>yolo11x-seg.pt</code> model is automatically downloaded by Ultralytics if not already available.</p>

<h3>Running Tumor Detection on Video</h3>
<pre><code>python detect.py
</code></pre>
<p>This processes <code>colonoscopy.mp4</code>, displays detections, and saves output as <code>output1.mp4</code>.</p>

<h3>Validation</h3>
<pre><code>python val.py
</code></pre>

<h2>Data Annotation</h2>
<p>
  The tumor masks were manually annotated using <a href="https://roboflow.com/" target="_blank" rel="noopener noreferrer">Roboflow</a>.
</p>


<h2>Colonoscopy Video</h2>
<p>The sample colonoscopy video used for testing can be downloaded from this link:</p>
<p><a href="https://drive.google.com/file/d/1r_w3DbZwS-oPaavZgdBXL5_q2OCbaxjX/view?usp=sharing" target="_blank">Download colonoscopy.mp4 from Google Drive</a></p>
<p class="note">Ensure the downloaded video is saved as <code>colonoscopy.mp4</code> in the root directory.</p>


<h2>Sample Output</h2>
<p>Below are the original colonoscopy frame and the tumor detection output side by side.</p>

<table style="border-collapse: collapse; width: 100%; table-layout: fixed;">
  <tr>
    <td style="text-align: center; padding: 10px;">
      <img src="https://github.com/anandakumar15/Colon-Polyps/blob/main/original.png" alt="Original Colonoscopy Frame" width="300" />
      <div style="font-style: italic; color: #555; margin-top: 5px; text-align: center;">   Original Colonoscopy Frame</div>
    </td>
    <td style="text-align: center; padding: 10px;">
      <img src="https://github.com/anandakumar15/Colon-Polyps/blob/main/detected.png" alt="Tumor Detection Output" width="300" />
      <div style="font-style: italic; color: #555; margin-top: 5px; text-align: center;">   Tumor Detection Output</div>
    </td>
  </tr>
</table>




</body>
</html>
