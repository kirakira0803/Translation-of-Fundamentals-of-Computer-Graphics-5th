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




# 目录

[一、 简介(Introduction)](#简介)

[1.1 图形领域(Graphics Areas)](#图形领域)

[1.2 主要应用(Major Applications)](#主要应用)

[1.3 图形API(Graphics APIs)](#图形API)

[1.4 图形管线(Graphics Pipeline)](#图形管线)

[1.5 数值问题(Numerical Issues)](#数值问题)

[1.6 效能(Efficiency)](#效能)

[1.7 设计和编码图形程序(Designing and Coding Graphics Programs)](#设计和编码图形程序)

![image](https://user-images.githubusercontent.com/41580525/158318705-27998ab7-0fc3-4d54-899c-9910dd2b7c48.png)

# 简介

计算机图形学（Computer Graphics）一词指的是任何情境下使用计算机创建和处理图像的一门学科。这本书介绍了各种算法和数学工具用来创建各种图像——逼真的视觉效果，信息丰富的技术插图或优美的计算机动画。图形可以是二维或者三维的;图像可以是完全人工合成的或者处理后产生的。这本书的内容包含了一些相关的算法和数学知识，主要讲解的是那些用来生成三维物体和场景的合成图像的相关知识。

实际上，做计算机图形学不可避免地需要了解一些特定的知识，比如硬件、文件格式，通常还需要有一两个图形**API**（见1.3节）。计算机图形学是一个快速发展的领域，所以它的细节知识是在不断地前进深入的。因此，在这本书中我们会尽最大努力避免对任何特定的硬件或**API**进行讲解，同时鼓励读者为其软件和硬件环境提供相关文档来补充本书内容。幸运的是，计算机图形学有足够多的标准术语和概念，本书中的讨论应该能很好地适合大部分环境。

本章定义了一些计算机图形学的基本术语，并且提供了一些历史背景以及与其相关的资料。

[返回目录](#目录) [返回本章开头](#简介)

## 图形领域

在任何领域强加类别都是危险的，但是大多数图形学从业者认为计算机图形学有以下几个主要领域：

<strong>· 建模（Modeling）</strong>是一种可以被存储在计算机中的形状和外观的数学表达。举个简单的例子，一个咖啡杯可以被描述为一组有序的3D顶点，一些连接这些点的插值规则和一个描述光线如何和咖啡杯相互作用的反射模型。

<strong>· 渲染（Rendering）</strong>是从艺术中继承的一个术语，涉及到如何从3D模型中创建出着色图像。

<strong>· 动画（Animation）</strong>是一种通过一系列连续的图像来创造运动错觉的技术。动画使用了建模和渲染，但比起这两者还需要关注如何处理物体随着时间运动变化的问题，而这在基础建模和渲染中通常不会被关注。

这里还有很多其他领域涉及计算机图形学，而对它们是否属于图形学核心领域这个问题每个人有不同的观点，但至少这些领域都将在书中被提及，这些相关领域包括：

<strong>· 用户交互（User interaction）</strong>处理输入设备(如鼠标和平板电脑)和应用程序的接口，并以图像或者其他形式反馈给用户。在历史上，这个领域和图形学相关主要是因为图形学研究人员对这些现在无所不在的输入/ 输出设备接触得早。

<strong>· 虚拟现实（Virtual reality）</strong>尝试让用户在3D虚拟世界中有沉浸式体验。这通常至少需要立体图形和对头部运动的响应，而对于真正的虚拟现实来说，还应该提供声音和力的反馈。因为这个领域需要先进的3D图形和显示技术，所以它通常与图形学密切相关。

<strong>· 可视化（Visualization）</strong>尝试通过视觉显示让用户深入了解复杂信息。通常情况下，在可视化中往往需要解决图形学问题。

<strong>· 图片处理（Image processing）</strong>涉及处理2D图像，并用于图形和视觉领域。

<strong>· 三维扫描（Three-dimensional scanning）</strong>用于测距技术来构建精细的3D模型，这些模型对于创造丰富的视觉图像是很有用的，同时对这些模型的处理通常需要图形算法。

<strong>· 计算摄影（Computational photography）</strong>是使用计算机图形学，计算机视觉以及图像处理方法来实现抓拍物体，场景和环境的新方法。

[返回目录](#目录) [返回本章开头](#简介) [返回本节开头](#图形领域)

## 主要应用

几乎所有工作都可以在一定程度上使用到计算机图形学，但是计算机图形学主要的应用行业有以下几个：

<strong>· 电子游戏（Video games）</strong>越来越多地使用复杂的3D模型和渲染算法。

<strong>· 卡通（Cartoons）</strong>通常直接从3D模型渲染而来，很多传统的2D动画使用了3D模型渲染的背景，这使得持续移动的观察点无需依靠艺术家的大量创作。

<strong>· 视觉效果（Visual effects）</strong>使用了几乎所有类型的计算机图形学技术。几乎每一部现代电影都使用了数字合成技术将背景和单独拍摄的前景叠加在一起，许多电影还使用3D建模和动画来创造人工合成的环境、物体和甚至大部分观众以为是真实存在的角色。

<strong>· 动画电影（Animated films）</strong>使用了很多和视觉效果一样的技术，但不需要做成特别逼真的图像。

<strong>· CAD/CAM</strong>代表计算机辅助设计和计算机辅助制造。这些领域使用计算机技术在计算机上设计零件和产品，然后使用这些虚拟设计来指导制造过程。例如，很多机械零件在3D计算机建模软件包中设计，然后由计算机控制在铣削设备上自动生产。

<strong>· 仿真（Simulation）</strong>可以被认为是精确的电子游戏。例如，一个飞行模拟器使用复杂的3D图形来模拟驾驶飞机的体验。这样的仿真对于在对安全性要求高的初期训练(如驾驶)中十分有用，同时对经验丰富的老手进行情景训练(如成本太高或太危险而无法实际创建的特定消防灾害)也十分有帮助。

<strong>· 医学成像（Medical imaging）</strong>为被扫描的患者数据创建了有意义的图像。例如，一个计算机体层摄影（CT）数据集由一个存储密度值的大型3D矩阵组成。计算机图形学被用来创建阴影图像来帮助医生从这些数据中提取最显著的信息。

<strong>· 信息可视化（Information visualization）</strong>创建的数据图像未必是一张“自然的”视觉绘图。例如，十种不同商品的价格并没有明显的视觉上的描述，但聪明的图像技术可以帮助人类看到数据中的模式。

[返回目录](#目录) [返回本章开头](#简介) [返回本节开头](#主要应用)

## 图形API

使用<strong>图形库（Graphics Libraries）</strong>的一个关键部分是与图形API打交道。应用程序接口（API）是执行一组相关操作的标准函数集合，而图形API是执行一些与图形相关的操作的标准函数集合，例如将图像和3D曲面绘制到屏幕上的窗口中。
  每个图形程序都至少需要使用两个相关的API：用于视觉输出的图形API和用于从用户那里获取输入的用户界面API。目前，图形API和用户界面API主要有两种模式。第一种是集成方法，以JAVA为例，图形和用户界面工具包是集成的、可移植的软件包，同时作为语言的一部分它们得到了充分的标准化和支持。第二种是以Direct3D和OpenGL为代表的，其中的绘图命令是与C++等语言相关的软件库中的一部分，而用户交互软件是一个独立的实体，在不同的平台上可能会有差异。在后一种模式中，编写可移植的代码可能会存在一些问题，尽管对于简单的程序而言我们可以使用可移植库来封装特定系统的用户界面代码。
  但无论你选择哪一种模式的API，基本的图形调用方法是大致相同的，本书的概念也会是适用的。
  
[返回目录](#目录) [返回本章开头](#简介) [返回本节开头](#图形API)

## 图形管线

如今，每台台式计算机都拥有强大的<strong>3D图形管线（3D Graphics Pipeline）</strong>。这是一个特殊的软件/硬件子系统，可以有效地在透视图中绘制3D图元。通常，这些系统都经过针对性优化，可以处理具有共享顶点的三维三角形。使用管线中的基本操作可以将3D顶点位置映射到2D屏幕位置并对三角形进行着色，使它们看起来都很逼真，并且它们会以正确的前后顺序显示。
  如何以前后顺序有效地绘制三角形曾经是计算机图形学中最重要的研究问题，但现在几乎总是使用<strong>z缓冲区（z-buffer）</strong>来解决这个问题，而它其实是使用了一种特殊的内存缓存来暴力解决。
  事实证明，图形管线中使用的几何操作几乎完全可以在三个传统几何坐标轴和一个有助于透视投影的四维齐次坐标系中完成。这些四维坐标系使用4x4的矩阵和四维向量进行操作。因此，图形管线包含了许多用于高效处理和合成此类矩阵和向量的系统。这个四维坐标系是计算机科学中最微妙和美丽的结构之一，它无疑是学习计算机图形学时要跨越的最大障碍，每本图形学书籍的第一部分都会有大篇幅涉及这些坐标。
  生成图像的速度在很大程度上取决于绘制的三角形数量，且因为在许多的应用程序中，它的交互性比视觉质量更加重要，所以有必要尽量减少用于表现模型的三角形数量。此外，如果从远处观察模型，则与近距离观察模型相比需要的三角形更少，这表明对于一个模型使用不同的细节层次（LOD）也是十分有用的。
  
[返回目录](#目录) [返回本章开头](#简介) [返回本节开头](#图形管线)

## 数值问题

许多图形程序实际上只是3D数值代码，在这类项目中，数值问题往往至关重要。在过去，我们很难以健壮可移植的方式处理此类问题，因为机器对于数值有不同的内部表示，更糟糕的是，它们会以不同而且不兼容的方式处理异常。幸运的是，几乎所有现代计算机都符合<strong>IEEE浮点数表示法（IEEE Standards Association，1985）</strong>，这使得程序员可以对如何处理某些数值条件做出许多方便的假设。
  虽然IEEE浮点数表示法在编码数值算法中有很多有用的功能，但对于图形学中遇到的大多数情况，只有少数几个功能是至关重要的。首先，同时也是最重要的一点，那就是要理解在IEEE浮点表示法中，实数有三个“特殊”值：
  
  ### 1. Infinity（∞）.
  这是一个大于所有其他有效数字的数字。
  ### 2. Minus infinity（-∞）
  这是一个小于所有其他有效数字的数字。
  ### 3. Not a number（NaN）
  这是一个无效数字，由未定义结果的操作产生，比如说零除以零。

IEEE浮点数表示法的设计者做出了一些对程序员来说非常方便的设计，其中许多与上述三个特殊值有关，用于处理除零异常等。在这些情况下，异常会被记录，但在大部分情况下，程序员可以忽略该异常，更具体的说，对于任何正实数a，以下的规则会涉及到无穷大值的除法

![image](https://user-images.githubusercontent.com/41580525/158379853-364adc0a-3066-40f1-b00b-2cb19ecec346.png)               ![image](https://user-images.githubusercontent.com/41580525/158380199-38f8eba7-fb7a-4de3-9004-589ee13887c5.png)

其他涉及无穷大值操作的结果基本与预期相同，即同样对于正实数a，有如下的规则：

![image](https://user-images.githubusercontent.com/41580525/158381060-2d3d6be0-ab54-4085-8101-7bc09cbda69f.png)

涉及无限值的布尔表达式中的规则也与预想的一样：

  ### 1. 所有有限的有效数字都小于+∞。
  ### 2. 所有有限的有效数字都大于-∞。
  ### 3. -∞小于+∞。

涉及具有NaN值的表达式的规则也很简单：

  ### 1. 任何包含NaN的算术表达式都会产生NaN。
  ### 2. 任何涉及NaN的布尔表达式的值都为假。

也许IEEE浮点表示法最有用的方面在于如何处理除零的问题；对于任何正实数a，以下涉及的规则都适用：

![image](https://user-images.githubusercontent.com/41580525/158382588-cf735f78-b151-47dd-9bb3-6f80b3ab093a.png)![image](https://user-images.githubusercontent.com/41580525/158383273-8d6dbe13-496f-445a-98e7-3fdb5f5eaad2.png)

如果程序员利用IEEE规则，那么许多数值计算会变得简单。例如，我们可以考虑表达式：

![image](https://user-images.githubusercontent.com/41580525/158383621-5cd3b267-3136-4793-81b8-66fa91e1bacd.png)

电阻和透镜都会出现这样的表达式，如果被零除会导致程序崩溃（在使用IEEE浮点表示法以前的许多系统都是如此），则需要两个if语句来检查b或c的更小者或零值。而对于IEEE浮点表示法来说，如果b或c为零，我们将根据需要获得a的零值。另一种避免特殊判断检查的常见技术是利用NaN的布尔属性，我们可以考虑以下的代码段：

![image](https://user-images.githubusercontent.com/41580525/158384347-5ca32c89-0bea-4f73-9678-69dfff98a7f1.png)

这里函数f(x)可能返回“不好”的值，例如∞或者NaN，但if条件还是可以完成判断：a = NaN或者a = -∞就返回false，a = +∞那么就返回true，而无需进行特殊判断，这使得程序更小更健壮也更高效。

[返回目录](#目录) [返回本章开头](#简介) [返回本节开头](#数值问题)

## 效能

没有任何神奇的魔法能使得代码变得更高效，效率是通过谨慎的权衡来获得的，对于不同的体系结构，这些取舍选择是不同的。然而，可以预见的是，在未来程序员应该会更多地关注内存访问模式，而不是操作数字。这与20年前的思路是相反的，这种切换之所以会发生，其实是因为内存的速度跟不上处理器的速度，而由于这一趋势仍在继续，限制内存使用以及统一内存访问对于优化的重要性只会上升。
  使代码快速运行的合理方法是按以下顺序优化代码，并且只采用我们需要的步骤：
  ### 1. 以最简单的方式编写代码，根据需要动态计算中间结果，而不是存储它们。
  ### 2. 以优化模式编译代码。
  ### 3. 使用现有的任何分析工具来发现关键瓶颈。
  ### 4. 检查数据结构，寻找改进局部的方法，如果可能的话，使数据单元大小和目标体系结构上的缓存/页面大小匹配。
  ### 5. 如果分析结果揭示了数值计算中的瓶颈，请检查编译器生成的汇编代码是否有效率上的损失，并且重新编写源代码以解决您发现的任何问题。
这些步骤中最重要的是第一步，大多数“优化”都会在不加快速度的情况下使得代码可读性变差。此外，预先优化代码所花的时间通常更适合用于纠正错误或者添加功能。同时，也要注意一些来自旧代码的支持性。一些经典的技巧，例如使用整数代替实数，可能不会再带来速度上的提升，因为现代CPU通常可以像执行整数运算一样快速的执行浮点运算。不管在任何情景下，我们都需要对代码进行分析，相信对于任何特定机器和编译器的优化都会给我们带来好处。

[返回目录](#目录) [返回本章开头](#简介) [返回本节开头](#效能)

## 设计和编码图形程序

在图形编程中，某些策略通常很有用。在本节中，我们将提供一些建议，在学习本书的过程中，您可能会发现这些建议很有用。

![image](https://user-images.githubusercontent.com/41580525/158394870-3131b9bf-78cc-408a-ae5d-5abd3eee0605.png)![image](https://user-images.githubusercontent.com/41580525/158394906-cafa8f89-c1ae-4935-9d6b-887789b986ca.png)

### 类的设计

任何图形程序的关键部分都是为几何实体（如向量和矩阵）以及图形实体（如RGB颜色和图像）提供良好的类或例程，这些例程应该尽可能干净高效。一个常见的设计问题是位置和位移是否应该是两个单独的类别，因为他们有不同的操作；例如，位置乘以一半没有几何意义，但是位移乘以一半有几何意义（Goldman，1985；DeRose，1989）。在这个问题上几乎没有达成一致意见，而这个问题可能会在图形学从业者中引发数小时的激烈辩论，但为了举例，让我们先假设我们对它们不做出区分。
  这意味着要编写的基本类包括：
  
  <strong>· vector2.</strong>存储x和y分量的2D向量类。它将这些分量存储在长度为2的数组中，以便能够很好地支持索引操作符。同时，它还应该包括向量加法、向量减法、点积、叉积、标量乘法和标量除法的运算。
  <strong>· vector3.</strong>一个类似于vector2的3D向量类。
  
  <strong>· hvector.</strong>一个有四个分量的齐次向量（见第8章）。
  
  <strong>· rgb.</strong>一个能存储三个分量的RGB颜色。它还应该包括RGB加法、RGB减法、RGB乘法、标量乘法和标量除法的运算。
  
  <strong>· transform.</strong>一个用于变换的4x4矩阵。它应该包括矩阵乘法和成员函数，以应用于位置、方向和表面法向量。如第7章所示，这些都是不同的。
  
  <strong>· image.</strong>一个带有输出操作的RGB像素的二维数组。
  
此外，您还有可能根据需要为区间、正交基和坐标系添加类。

![image](https://user-images.githubusercontent.com/41580525/158401019-25d32138-eeb4-46c6-b95e-1f52977728ce.png)

[返回目录](#目录) [返回本章开头](#简介) [返回本大节开头](#设计和编码图形程序) [返回本小节开头](#类的设计)

### 单精度浮点数 vs 双精度浮点数

现代的体系结构表明，降低内存使用和统一内存访问是提高效率的关键。因此，我们应该尽量使用单精度浮点数，然而，为了避免数值问题，我们应该使用双精度计算。这种权衡取决于程序，但如果在类的定义中有一个默认值是最好的。

![image](https://user-images.githubusercontent.com/41580525/158403700-8497b972-fbfb-4904-84f7-cd7884127dec.png)![image](https://user-images.githubusercontent.com/41580525/158405860-a2b26d6e-c36a-458d-afce-08d536a5dcec.png)

[返回目录](#目录) [返回本章开头](#简介) [返回本大节开头](#设计和编码图形程序) [返回本小节开头](#单精度浮点数\ vs\ 双精度浮点数)

### 调试图形程序

如果你四处打听，你可能会发现，随着程序员越来越有经验，他们越来越少使用传统的调试器。其中一个原因是使用这样的调试器来调试复杂程序比调试简单程序更不方便。另外一个原因是他们会犯的最麻烦的错误是被执行的概念性错误，这会使得他们浪费大量的时间去逐步检查变量而没有发现这种情况。我们发现有几种策略在程序调试中特别有用。

<strong>科学方法（The Scientific Method）</strong>

在图形程序中，有一种代替传统调试的方法，这种方法非常有用。它的缺点是，它与计算机程序员在职业生涯早期被教导不要做的事情非常地相似，因此如果你这样做，你可能会觉得有点“淘气”：我们创建一个图像，并且观察它有什么问题。然后，我们提出一个关于问题起因的假设，并且对其进行检验。例如，在光线追踪程序中，我们可能有许多看起来有些随机的暗像素。这是大多数人在写光线追踪器时遇到的经典“暗疮”问题。传统的调试在这里反而没有帮助；相反，我们必须意识到阴影射线照射到了正在被着色的表面。我们可能会注意到暗点的颜色是环境色，所以缺少的是直接照明。在阴影中直接照明会被关闭，因此您可能会假设这些点未被正确标记，它们被错误地标记为了“在阴影之中”。为了验证这个假设，我们可以关闭阴影检查并重新编译。这表明它是虚假的阴影测试，我们可以继续检查工作。这种方法有时候可以有良好实践效果的关键原因是，我们从来不需要发现错误的值或者真正确定哪里有概念性错误。相反，我们只是在实验上缩小了概念错误的范围。通常情况下，只需要进行几次这样的试验就可以跟踪发现问题，这种类型的调试是令人感到舒适的。

<strong>图像作为编码调试输出（Images as Coded Debugging Output）</strong>

在许多情况下，从图形程序获取调试信息的最简单渠道是输出图像本身。如果您想知道某个用于在每个像素上进行计算的变量值，您可以临时修改程序，将该值直接复制到输出图像中，并跳过通常会进行的其余计算。例如，如果怀疑表面法线导致了着色问题，可以将法线向量直接复制到图像（x变为红色，y变为绿色，z变为蓝色），从而生成计算中实际使用的向量颜色编码图示。或者，如果您怀疑某个特定值有时超出其有效范围，请让您的程序在出现这种情况的地方写入红色像素以标示在输出图像上。其他常见的技巧包括使用明显的颜色（当它们应该是不可见的）绘制物体的背面，根据物体的编号为图像着色，或根据计算次数为像素着色。

[返回目录](#目录) [返回本章开头](#简介) [返回本大节开头](#设计和编码图形程序) [返回本小节开头](#调试图形程序)






  
  
