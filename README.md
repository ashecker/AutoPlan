# AutoPlan
本项目主要完成了在军事领域下基于大模型的复杂任务规划和执行，使用到了改进的react技术进行长链条的agent执行。代码仍在整理，一个月内可以上传
 首先本仓库要感谢尹俊希老帅哥的大力支持，为本项目做出了非常大的帮助
基本原理：
本项目第一版原理如下图，第二版将第一版进行了数据蒸馏，解决了第一版存在的多轮对话，显存、推理效率，简单任务执行和简单对话等等任务。
![image](https://github.com/LDLINGLINGLING/AutoPlan/assets/47373076/e6087bbd-b1cf-49de-a3d2-b84eb24da9fa)

数据集：
train_plan.json和test_plan.json分别为进行任务规划的训练数据集和测试数据集。可以放入qwen1/qwen1.5中训练，训练后qwen模型可获得任务规划能力。
![image](https://github.com/LDLINGLINGLING/AutoPlan/assets/47373076/5b01b9d4-bf52-4502-b910-c3f8a8851417)

将main.py文件中allparams_split_task_chain的default值改为训练后的任务规划qwen模型。将execute_model_path改为qwen72b的的模型地址，execute_reflexion改为false。其他不变，运行即可获得任务规划和执行能力。

数据集2：
train_react.josn和test_react.json分别为对任务规划和任务执行两个模型蒸馏出来的数据，并且进行人工标注的数据。
将train_react.json放到qwen1/qwen1.5内进行训练，可将任务规划和任务执行能力导入同一个模型，建议使用qwen1.5 14b进行训练.
训练完成后将main.py文件中allparams_split_task_chain的default值改为false。将execute_model_path改为以上模型训练的模型地址，execute_reflexion改为false。
推理可得一个模型同时获得任务规划和任务执行两个效果。
任务规划阶段效果如下：
<img width="1280" alt="294754660-1aafe21f-f39c-4a36-9002-c27e3eb9f5ce" src="https://github.com/LDLINGLINGLING/AutoPlan/assets/47373076/485d5a8f-b492-4aec-8a0f-f1bcc1853a4e">

任务执行阶段效果如下:
<img width="981" alt="294754670-46c7ed17-197f-487a-b9bc-893c49eaba36" src="https://github.com/LDLINGLINGLING/AutoPlan/assets/47373076/389d22fe-e1e5-4595-8de9-d0683524bd93">


续上
![image](https://github.com/LDLINGLINGLING/AutoPlan/assets/47373076/6f2b1dcc-4572-425a-8e7b-04a8a73e363e)



