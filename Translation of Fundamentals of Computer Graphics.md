![image](https://user-images.githubusercontent.com/41580525/158318589-f6fb9aa9-35a6-4cd2-a895-75e8488cb75f.png)








![image](https://user-images.githubusercontent.com/41580525/158318649-16f32ee8-fc69-4051-abe6-3ceb691a872c.png)

Fifth edition published 2022 by CRC Press

6000 Broken Sound Parkway NW, Suite 300, Boca Raton, FL 33487-2742

and by CRC Press

2 Park Square, Milton Park, Abingdon, Oxon, OX14 4RN

© 2022 Taylor & Francis Group, LLC

CRC Press is an imprint of Taylor & Francis Group, LLC

Reasonable efforts have been made to publish reliable data and information, but
the author and publisher cannot assume responsibility for the validity of all
materials or the consequences of their use. The authors and publishers have
attempted to trace the copyright holders of all material reproduced in this
publication and apologize to copyright holders if permission to publish in this
form has not been obtained. If any copyright material has not been acknowledged
please write and let us know so we may rectify in any future reprint.

Except as permitted under U.S. Copyright Law, no part of this book may be
reprinted, reproduced, transmitted, or utilized in any form by any electronic,
mechanical, or other means, now known or hereafter invented, including
photocopying, microfilming, and recording, or in any information storage or
retrieval system, without written permission from the publishers.

For permission to photocopy or use material electronically from this work,
access www.copyright.com or contact the Copyright Clearance Center, Inc. (CCC),
222 Rosewood Drive, Danvers, MA 01923, 978-750-8400. For works that are not
available on CCC please contact mpkbookspermissions@tandf.co.uk

Trademark notice: Product or corporate names may be trademarks or registered
trademarks and are used only for identification and explanation without intent
to infringe.

Library of Congress Cataloging‑in‑Publication Data

Names: Marschner, Steve, author. \| Shirley, Peter, author.

Title: Fundamentals of computer graphics / Steve Marschner, Peter Shirley.
Description: 5th edition. \| Boca Raton: CRC Press, 2021. \| Includes
bibliographical references and index. Identifiers: LCCN 2021008492 \| ISBN
9780367505035 (hardback) \| ISBN 9781003050339 (ebook)

Subjects: LCSH: Computer graphics.

Classification: LCC T385 .M36475 2021 \| DDC 006.6—dc23 LC record available at
https://lccn.loc.gov/2021008492

ISBN: 978-0-367-50503-5 (hbk)

ISBN: 978-0-367-50558-5 (pbk)

ISBN: 978-1-003-05033-9 (ebk)

Typeset in Times by codeMantra




目录

[一、 简介(Introduction)](#简介(Introduction))

[1.1 图形领域(Graphics Areas)](#图形领域（Graphics Areas）)

[1.2 主要应用(Major Applications)](#主要应用（Major Applications）)

[1.3 图形API(Graphics APIs)](#图形API（Graphics APIs）)

![image](https://user-images.githubusercontent.com/41580525/158318705-27998ab7-0fc3-4d54-899c-9910dd2b7c48.png)

# 简介（Introduction）

计算机图形学（Computer
Graphics）一词指的是任何使用计算机创建和处理图像的一门学科。这本书介绍了各种算法和数学工具用来创建各种图像——逼真的视觉效果，信息丰富的技术插图或优美的计算机动画。图形可以是二维或者三维的;图像可以是完全人工合成的或者是处理后产生的。这本书的内容包含了一些相关的算法和数学知识，主要讲解的是那些用来生成三维物体和场景的合成图像的相关知识。

实际上，做计算机图形学不可避免地需要了解一些特定的知识，比如硬件、文件格式，通常还需要有一两个图形**API**（见1.3节）。计算机图形学是一个快速发展的领域，所以它的细节知识是在不断地前进深入的。因此，在这本书中我们会尽最大努力避免对任何特定的硬件或**API**进行讲解，同时鼓励读者为其软件和硬件环境提供相关文档来补充本书内容。幸运的是，计算机图形学有足够多的标准术语和概念，本书中的讨论应该能很好的适合大部分环境。

本章定义了一些计算机图形学的基本术语，并且提供了一些历史背景以及与其相关的信息。

## 图形领域（Graphics Areas）

在任何领域强加类别都是危险的，但是大多数图形学从业者认为计算机图形学有以下几个主要领域：

<strong>·建模（Modeling）</strong>是一种可以被存储在计算机中的形状和外观的数学表
达。举个简单的例子，一个咖啡杯可以描述为一组有序的3D顶点，以
及一些连接这些点的插值规则和一个描述光线如何和咖啡杯相互作用的 反射模型。

<strong>·渲染（Rendering）</strong>是从艺术中继承的一个术语，涉及到如何从3D模型
中创建出着色图像。

<strong>·动画（Animation）</strong>是一种通过一系列连续的图像来创造 运动错觉的
技术。动画使用了建模和渲染，但增加了随着时间移动变化的关键性问
题，这在基础建模和渲染中通常不会被处理。

这里还有很多其他的领域涉及计算机图形学，而对它们是否属于图形学核心领域这个问题每个人有不同的观点，但至少这些领域都将在书中被提及，这些相关领域包括：

<strong>·用户交互（User interaction）</strong>处理输入设备(如鼠标和平板电脑)和应用
程序的接口，并以图像或者其他形式反馈给用户。在历史上，这个领域
和图形学相关主要是因为图形学研究人员对这些现在无所不在的输入/ 输出设备接触的早。

<strong>·虚拟现实（Virtual reality）</strong>尝试让用户在3D虚拟世界中有沉浸式体验。
这通常至少需要立体图形和对头部运动的响应，而对于真正的虚拟现实
来说，还应该提供声音和力的反馈。因为这个领域需要先进的3D图形
和显示技术，所以它通常与图形学密切相关。

<strong>·可视化（Visualization）</strong>尝试通过视觉显示让用户深入了解复杂信息。
通常情况下，在可视化中往往需要解决图形学问题。

<strong>·图片处理（Image processing）</strong>涉及处理2D图像，并用于图形和视觉领 域。

<strong>·三维扫描（Three-dimensional scanning）</strong>用于测距技术来建造精细的3D
模型，这些模型对于创造丰富的视觉图像是很有用的，同时这些模型的
处理通常需要图形算法。

<strong>·计算摄影（Computational photography）</strong>是使用计算机图形学，计算机
视觉以及图像处理方法来实现抓拍物体，场景和环境的新方法。

## 主要应用（Major Applications）

几乎所有工作都可以在一定程度上使用到计算机图形学，但是计算机图形学主
要的应用行业有以下几个：

<strong>·电子游戏（Video games）</strong>越来越多地使用复杂的3D模型和渲染算法。

<strong>·卡通（Cartoons）</strong>通常直接从3D模型渲染而来，很多传统的2D动画使
用了3D模型渲染的背景，这使得持续移动的观察点无需艺术家的大量 创作。

<strong>·视觉效果（Visual effects）</strong>几乎使用了所有类型的计算机图形学技术。
几乎每一部现代电影都使用了数字合成技术将背景和单独拍摄的前景叠
加在一起。许多电影还使用3D建模和动画来创造人工合成的环境、物
体，甚至大部分观众以为是真实存在的角色。

<strong>·动画电影（Animated films）</strong>使用了很多和视觉效果一样的技术，但不
需要做成特别逼真的图像。

<strong>·CAD/CAM</strong>代表计算机辅助设计和计算机辅助制造。这些领域使用计算
机技术在计算机上设计零件和产品，然后使用这些虚拟设计来指导制造
过程。例如，很多机械零件在3D计算机建模软件包中设计，然后自动
在计算机控制的铣削设备上生产。

<strong>·仿真（Simulation）</strong>可以被认为是精确的视频游戏。例如，一个飞行模
拟器使用复杂的3D图形来模拟驾驶飞机的体验。这样的仿真对于在对
安全性要求高的初期训练(如驾驶)中十分有用，同时对经验丰富的老手
进行情景训练(如成本太高或太危险而无法实际创建的特定消防灾害)也 十分有帮助。

<strong>·医学成像（Medical imaging）</strong>为被扫描的患者数据创建了有意义的图
像。例如，一个计算机体层摄影（CT）数据集由一个存储密度值的大型
3D矩阵组成。计算机图形学被用来创建阴影图像来帮助医生从这些数据
中提取最显著的信息。

<strong>·信息可视化（Information visualization）</strong>创建的数据图像未必是一张“自
然的”视觉绘图。例如，十种不同商品的价格并没有明显的视觉上的描
述，但聪明的图像技术可以帮助人类看到数据中的模式。

## 图形API（Graphics APIs）


