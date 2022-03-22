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

[二、 各种各样的数学(Miscellaneous Math)](#各种各样的数学)

[2.1 集合和映射(Sets and Mappings)](#集合和映射)

[2.2 解二次方程(Solving Quadratic Equations)](#解二次方程)

[2.3 三角学(Trigonometry)](#三角学)

[2.4 向量(Vectors)](#向量)

***

![image](https://user-images.githubusercontent.com/41580525/158318705-27998ab7-0fc3-4d54-899c-9910dd2b7c48.png)

# 简介

计算机图形学（Computer Graphics）一词指的是任何情境下使用计算机创建和处理图像的一门学科。这本书介绍了各种算法和数学工具用来创建各种图像——逼真的视觉效果，信息丰富的技术插图或优美的计算机动画。图形可以是二维或者三维的;图像可以是完全人工合成的或者处理后产生的。这本书的内容包含了一些相关的算法和数学知识，主要讲解的是那些用来生成三维物体和场景的合成图像的相关知识。

实际上，做计算机图形学不可避免地需要了解一些特定的知识，比如硬件、文件格式，通常还需要有一两个图形**API**（见1.3节）。计算机图形学是一个快速发展的领域，所以它的细节知识是在不断地前进深入的。因此，在这本书中我们会尽最大努力避免对任何特定的硬件或**API**进行讲解，同时鼓励读者为其软件和硬件环境提供相关文档来补充本书内容。幸运的是，计算机图形学有足够多的标准术语和概念，本书中的讨论应该能很好地适合大部分环境。

本章定义了一些计算机图形学的基本术语，并且提供了一些历史背景以及与其相关的资料。

## 1.1
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

## 1.2
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

## 1.3
## 图形API

使用<strong>图形库（Graphics Libraries）</strong>的一个关键部分是与图形API打交道。应用程序接口（API）是执行一组相关操作的标准函数集合，而图形API是执行一些与图形相关的操作的标准函数集合，例如将图像和3D曲面绘制到屏幕上的窗口中。
  每个图形程序都至少需要使用两个相关的API：用于视觉输出的图形API和用于从用户那里获取输入的用户界面API。目前，图形API和用户界面API主要有两种模式。第一种是集成方法，以JAVA为例，图形和用户界面工具包是集成的、可移植的软件包，同时作为语言的一部分它们得到了充分的标准化和支持。第二种是以Direct3D和OpenGL为代表的，其中的绘图命令是与C++等语言相关的软件库中的一部分，而用户交互软件是一个独立的实体，在不同的平台上可能会有差异。在后一种模式中，编写可移植的代码可能会存在一些问题，尽管对于简单的程序而言我们可以使用可移植库来封装特定系统的用户界面代码。
  但无论你选择哪一种模式的API，基本的图形调用方法是大致相同的，本书的概念也会是适用的。
  
[返回目录](#目录) [返回本章开头](#简介) [返回本节开头](#图形API)

## 1.4
## 图形管线

如今，每台台式计算机都拥有强大的<strong>3D图形管线（3D Graphics Pipeline）</strong>。这是一个特殊的软件/硬件子系统，可以有效地在透视图中绘制3D图元。通常，这些系统都经过针对性优化，可以处理具有共享顶点的三维三角形。使用管线中的基本操作可以将3D顶点位置映射到2D屏幕位置并对三角形进行着色，使它们看起来都很逼真，并且它们会以正确的前后顺序显示。
  如何以前后顺序有效地绘制三角形曾经是计算机图形学中最重要的研究问题，但现在几乎总是使用<strong>z缓冲区（z-buffer）</strong>来解决这个问题，而它其实是使用了一种特殊的内存缓存来暴力解决。
  事实证明，图形管线中使用的几何操作几乎完全可以在三个传统几何坐标轴和一个有助于透视投影的四维齐次坐标系中完成。这些四维坐标系使用4x4的矩阵和四维向量进行操作。因此，图形管线包含了许多用于高效处理和合成此类矩阵和向量的系统。这个四维坐标系是计算机科学中最微妙和美丽的结构之一，它无疑是学习计算机图形学时要跨越的最大障碍，每本图形学书籍的第一部分都会有大篇幅涉及这些坐标。
  生成图像的速度在很大程度上取决于绘制的三角形数量，且因为在许多的应用程序中，它的交互性比视觉质量更加重要，所以有必要尽量减少用于表现模型的三角形数量。此外，如果从远处观察模型，则与近距离观察模型相比需要的三角形更少，这表明对于一个模型使用不同的细节层次（LOD）也是十分有用的。
  
[返回目录](#目录) [返回本章开头](#简介) [返回本节开头](#图形管线)

## 1.5
## 数值问题

许多图形程序实际上只是3D数值代码，在这类项目中，数值问题往往至关重要。在过去，我们很难以健壮可移植的方式处理此类问题，因为机器对于数值有不同的内部表示，更糟糕的是，它们会以不同而且不兼容的方式处理异常。幸运的是，几乎所有现代计算机都符合<strong>IEEE浮点数表示法（IEEE Standards Association，1985）</strong>，这使得程序员可以对如何处理某些数值条件做出许多方便的假设。
  虽然IEEE浮点数表示法在编码数值算法中有很多有用的功能，但对于图形学中遇到的大多数情况，只有少数几个功能是至关重要的。首先，同时也是最重要的一点，那就是要理解在IEEE浮点表示法中，实数有三个“特殊”值：
  
  <strong> 1. Infinity（∞）.</strong>
  
  这是一个大于所有其他有效数字的数字。
  
  <strong> 2. Minus infinity（-∞）.</strong>
  
  这是一个小于所有其他有效数字的数字。
  
  <strong> 3. Not a number（NaN）.</strong>
  
  这是一个无效数字，由未定义结果的操作产生，比如说零除以零。

IEEE浮点数表示法的设计者做出了一些对程序员来说非常方便的设计，其中许多与上述三个特殊值有关，用于处理除零异常等。在这些情况下，异常会被记录，但在大部分情况下，程序员可以忽略该异常，更具体的说，对于任何正实数a，以下的规则会涉及到无穷大值的除法

![image](https://user-images.githubusercontent.com/41580525/158379853-364adc0a-3066-40f1-b00b-2cb19ecec346.png)               ![image](https://user-images.githubusercontent.com/41580525/158380199-38f8eba7-fb7a-4de3-9004-589ee13887c5.png)

其他涉及无穷大值操作的结果基本与预期相同，即同样对于正实数a，有如下的规则：

![image](https://user-images.githubusercontent.com/41580525/158381060-2d3d6be0-ab54-4085-8101-7bc09cbda69f.png)

涉及无限值的布尔表达式中的规则也与预想的一样：

  <strong> 1. 所有有限的有效数字都小于+∞。</strong>
  
  <strong> 2. 所有有限的有效数字都大于-∞。</strong>
  
  <strong> 3. -∞小于+∞。</strong>

涉及具有NaN值的表达式的规则也很简单：

  <strong> 1. 任何包含NaN的算术表达式都会产生NaN。</strong>
  
  <strong> 2. 任何涉及NaN的布尔表达式的值都为假。</strong>

也许IEEE浮点表示法最有用的方面在于如何处理除零的问题；对于任何正实数a，以下涉及的规则都适用：

![image](https://user-images.githubusercontent.com/41580525/158382588-cf735f78-b151-47dd-9bb3-6f80b3ab093a.png)![image](https://user-images.githubusercontent.com/41580525/158383273-8d6dbe13-496f-445a-98e7-3fdb5f5eaad2.png)

如果程序员利用IEEE规则，那么许多数值计算会变得简单。例如，我们可以考虑表达式：

![image](https://user-images.githubusercontent.com/41580525/158383621-5cd3b267-3136-4793-81b8-66fa91e1bacd.png)

电阻和透镜都会出现这样的表达式，如果被零除会导致程序崩溃（在使用IEEE浮点表示法以前的许多系统都是如此），则需要两个if语句来检查b或c的更小者或零值。而对于IEEE浮点表示法来说，如果b或c为零，我们将根据需要获得a的零值。另一种避免特殊判断检查的常见技术是利用NaN的布尔属性，我们可以考虑以下的代码段：

![image](https://user-images.githubusercontent.com/41580525/158384347-5ca32c89-0bea-4f73-9678-69dfff98a7f1.png)

这里函数f(x)可能返回“不好”的值，例如∞或者NaN，但if条件还是可以完成判断：a = NaN或者a = -∞就返回false，a = +∞那么就返回true，而无需进行特殊判断，这使得程序更小更健壮也更高效。

[返回目录](#目录) [返回本章开头](#简介) [返回本节开头](#数值问题)

## 1.6
## 效能

没有任何神奇的魔法能使得代码变得更高效，效率是通过谨慎的权衡来获得的，对于不同的体系结构，这些取舍选择是不同的。然而，可以预见的是，在未来程序员应该会更多地关注内存访问模式，而不是操作数字。这与20年前的思路是相反的，这种切换之所以会发生，其实是因为内存的速度跟不上处理器的速度，而由于这一趋势仍在继续，限制内存使用以及统一内存访问对于优化的重要性只会上升。
  使代码快速运行的合理方法是按以下顺序优化代码，并且只采用我们需要的步骤：
  
  <strong> 1. 以最简单的方式编写代码，根据需要动态计算中间结果，而不是存储它们。</strong>
  
  <strong> 2. 以优化模式编译代码。</strong>
  
  <strong> 3. 使用现有的任何分析工具来发现关键瓶颈。</strong>
  
  <strong> 4. 检查数据结构，寻找改进局部的方法，如果可能的话，使数据单元大小和目标体系结构上的缓存/页面大小匹配。</strong>
  
  <strong> 5. 如果分析结果揭示了数值计算中的瓶颈，请检查编译器生成的汇编代码是否有效率上的损失，并且重新编写源代码以解决您发现的任何问题。</strong>
  
这些步骤中最重要的是第一步，大多数“优化”都会在不加快速度的情况下使得代码可读性变差。此外，预先优化代码所花的时间通常更适合用于纠正错误或者添加功能。同时，也要注意一些来自旧代码的支持性。一些经典的技巧，例如使用整数代替实数，可能不会再带来速度上的提升，因为现代CPU通常可以像执行整数运算一样快速的执行浮点运算。不管在任何情景下，我们都需要对代码进行分析，相信对于任何特定机器和编译器的优化都会给我们带来好处。

[返回目录](#目录) [返回本章开头](#简介) [返回本节开头](#效能)

## 1.7
## 设计和编码图形程序

在图形编程中，某些策略通常很有用。在本节中，我们将提供一些建议，在学习本书的过程中，您可能会发现这些建议很有用。

![image](https://user-images.githubusercontent.com/41580525/158394870-3131b9bf-78cc-408a-ae5d-5abd3eee0605.png)![image](https://user-images.githubusercontent.com/41580525/158394906-cafa8f89-c1ae-4935-9d6b-887789b986ca.png)

### 1.7.1
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

### 1.7.2
### 单精度浮点数vs双精度浮点数

现代的体系结构表明，降低内存使用和统一内存访问是提高效率的关键。因此，我们应该尽量使用单精度浮点数，然而，为了避免数值问题，我们应该使用双精度计算。这种权衡取决于程序，但如果在类的定义中有一个默认值是最好的。

![image](https://user-images.githubusercontent.com/41580525/158403700-8497b972-fbfb-4904-84f7-cd7884127dec.png)![image](https://user-images.githubusercontent.com/41580525/158405860-a2b26d6e-c36a-458d-afce-08d536a5dcec.png)

[返回目录](#目录) [返回本章开头](#简介) [返回本大节开头](#设计和编码图形程序) [返回本小节开头](#单精度浮点数vs双精度浮点数)

### 1.7.3
### 调试图形程序

如果你四处打听，你可能会发现，随着程序员越来越有经验，他们越来越少使用传统的调试器。其中一个原因是使用这样的调试器来调试复杂程序比调试简单程序更不方便。另外一个原因是他们会犯的最麻烦的错误是被执行的概念性错误，这会使得他们浪费大量的时间去逐步检查变量而没有发现这种情况。我们发现有几种策略在程序调试中特别有用。

<strong>科学方法（The Scientific Method）</strong>

在图形程序中，有一种代替传统调试的方法，这种方法非常有用。它的缺点是，它与计算机程序员在职业生涯早期被教导不要做的事情非常地相似，因此如果你这样做，你可能会觉得有点“淘气”：我们创建一个图像，并且观察它有什么问题。然后，我们提出一个关于问题起因的假设，并且对其进行检验。例如，在光线追踪程序中，我们可能有许多看起来有些随机的暗像素。这是大多数人在写光线追踪器时遇到的经典“暗疮”问题。传统的调试在这里反而没有帮助；相反，我们必须意识到阴影射线照射到了正在被着色的表面。我们可能会注意到暗点的颜色是环境色，所以缺少的是直接照明。在阴影中直接照明会被关闭，因此您可能会假设这些点未被正确标记，它们被错误地标记为了“在阴影之中”。为了验证这个假设，我们可以关闭阴影检查并重新编译。这表明它是虚假的阴影测试，我们可以继续检查工作。这种方法有时候可以有良好实践效果的关键原因是，我们从来不需要发现错误的值或者真正确定哪里有概念性错误。相反，我们只是在实验上缩小了概念错误的范围。通常情况下，只需要进行几次这样的试验就可以跟踪发现问题，这种类型的调试是令人感到舒适的。

<strong>把图像作为编码调试输出（Images as Coded Debugging Output）</strong>

在许多情况下，从图形程序中获取调试信息的最简单渠道是输出图像本身。如果您想知道某个用于在每个像素上进行计算的变量值，您可以临时修改程序，将该值直接复制到输出图像中，并跳过通常会进行的其余计算。例如，如果怀疑表面法线导致了着色问题，可以将法线向量直接复制到图像（x变为红色，y变为绿色，z变为蓝色），从而使之生成计算中实际使用的向量颜色编码图示。或者，如果您怀疑某个特定值有时超出其有效范围，请让您的程序在出现这种情况的地方写入红色像素以标示在输出图像上。其它常见的技巧包括使用明显的颜色绘制物体的背面（当它们应该是不可见的），根据物体的编号为图像着色，或根据计算次数为像素着色。

<strong>使用调试器（Using a Debugger）</strong>

仍然有一些情景，尤其是当科学方法似乎导致了矛盾时，没有什么可以代替精确观察正在发生的事情。问题在于，图形程序通常涉及对同一行代码的多次执行（例如，每像素一次，或每三角形一次），这使得从一开始就在调试器中逐步执行完全不切实际，最困难的错误往往只出现在复杂的输入中。
  一个有用的方法是为bug“设置陷阱”。首先，确保你的程序是确定性的，在一个线程中运行它，并确保所有随机数都是从固定种子中计算出来的。然后，找出哪一个像素或三角形显示错误，并在您怀疑代码不正确的地方之前加入一条语句，该语句将仅针对可疑情况执行。例如，如果你发现了像素（126,247）显示错误，那么添加：

![image](https://user-images.githubusercontent.com/41580525/158724001-5d487b77-8606-4f32-9de3-aabe91713cde.png)![image](https://user-images.githubusercontent.com/41580525/158724034-ca7618c0-91f0-4288-828e-77f16ff6a95c.png)

如果在print语句上设置了断点，那么就可以在计算这个像素之前进入调试器。有些调试器具有“条件断点”功能，可以在不修改代码的情况下实现相同的功能。
  在程序崩溃的情况下，传统的调试器有助于确定崩溃的位置。然后，您应该在程序中使用断言和重新编译进行回溯，以找到程序出错的地方。这些断言应该留在程序中，以便测试将来可能发生的bug。这意味着避免了传统的单步执行过程，因为这种传统方式不会向程序添加有用的断言。

<strong>用于调试的可视化数据（Data Visualization for Debugging）</strong>

通常，你会很难理解你的程序在做什么，因为它在最终出错之前会计算很多中间结果。这种情况类似于一个处理大量数据的科学实验，有一个解决方法是通用的：为自己绘制好布局和插图，以理解数据的意义。例如，在光线追踪器中，您可以编写代码来可视化光线树（ray trees），以便查看哪些路径对像素有影响，或者在图像重采样中，您可以绘制显示所有从输入中采样的点的图。当需要优化程序时，花时间在编写代码以可视化程序内部上也会有助于更好地理解其行为。

![image](https://user-images.githubusercontent.com/41580525/158729933-80056670-9e74-4c67-b1cd-cb2510e84ffe.png)

<strong>笔记</strong>

关于软件工程的讨论受到了Effective C++ series（Meyers, 1995, 1997）, the Extreme Programming movement（Beck & Andres, 2004）和The Practice of Programming（Kernighan & Pike, 1999）的影响。对实验调试的讨论则是基于Steve Parker的讨论。
  有许多与计算机图形学相关的年度会议，包括ACM SIGGRAPH和SIGGRAPH Asia，Graphics Interface，the Game Developers Conference（GDC），Eurographics，Pacific Graphics，High Performance Graphicsthe Eurographics Symposium on Rendering，和IEEE VisWeek。通过网络搜索它们的名字可以很容易地找到。

[返回目录](#目录) [返回本章开头](#简介) [返回本大节开头](#设计和编码图形程序) [返回本小节开头](#调试图形程序)

***

![image](https://user-images.githubusercontent.com/41580525/158731005-0d1b9478-44c9-452c-a1fb-498d4fffabab.png)

# 各种各样的数学

图形学的大部分内容只是将数学转换为代码，数学逻辑越清晰，生成的代码也越简明；这本书的大部分内容都集中在使用适合这项工作的数学工具。本章回顾了高中和大学数学中的各种数学，旨在更多地作为参考而非指导。它看起来像是一个大杂烩式的主题，事实的确如此；下文每个会提到的数学知识点是因为它在“标准”数学中有点不寻常，或在图形学中非常重要，又或者它通常不是从几何角度来处理的。除了对本书中使用的数学符号进行回顾外，本章还强调了标准本科课程中有时会忽略的几点，例如三角形上的重心坐标。本章无意对材料进行严格地处理；相反，会更强调直觉和几何解释。线性代数的讨论被推迟到第六章讨论变换矩阵之前。鼓励读者浏览本章，以熟悉所涵盖的数学知识点，并根据需要查阅。本章末尾的练习可能有助于确定哪些知识点需要复习。

## 2.1
## 集合和映射

映射，也称为函数，是数学和编程的基础。就像程序中的函数一样，数学中的映射会接受一种类型的参数，并将其映射到（返回）特定类型的对象。在程序中，我们称之为“类型”；在数学中，我们称之为集合。当我们有一个对象是集合的成员时，我们使用∈符号，例如：a ∈ <strong>S</strong>，它可以理解为“a是集合<strong>S</strong>的成员”。给定两个任意集合<strong>A</strong>和<strong>B</strong>，我门可以通过取这两个集合的笛卡尔积来创建第三个集合，表示为<strong>A</strong> × <strong>B</strong>。这个集合<strong>A</strong> × <strong>B</strong>由所有可能的有序对（a，b）组成，其中a ∈ <strong>A</strong>，b ∈ <strong>B</strong>。同时，为了简化我们使用<strong>A</strong>²来表示<strong>A</strong> × <strong>A</strong>。我们可以扩展笛卡尔积，从三个集合中创建一组所有可能的有序三元组，以此类推，我们可以从任意n个集合中创建有序n元组。
  常见又有趣的集合包括：
  
  ![image](https://user-images.githubusercontent.com/41580525/158835553-6d8eee1a-8f1f-4cf9-86b0-db1ba8dcd108.png)——实数集合；
  
  ![image](https://user-images.githubusercontent.com/41580525/158835001-970d42c9-984b-4729-aed2-6716f014ef27.png)——非负实数（包括零）；
  
  ![image](https://user-images.githubusercontent.com/41580525/158835075-eae35ae2-74fa-4b53-90c6-852c3083014a.png)——二维平面上的有序对；
  
  ![image](https://user-images.githubusercontent.com/41580525/158835207-ed0bba00-e177-4f58-96ff-77ca589de493.png)——n维笛卡尔空间中的点；
  
  ![image](https://user-images.githubusercontent.com/41580525/158835267-1a4697dc-3924-4e11-a7d1-214c06a55a6d.png)——整数；
  
  ![image](https://user-images.githubusercontent.com/41580525/158835375-3a11b683-1855-40cd-a298-97bdae1c09c7.png)——单位球体上的一组三维点（<strong>R</strong>³中的点）
  
请注意，尽管<strong>S</strong>²由嵌入三维空间的点组成，但它位于可以用两个变量参数化的曲面上，因此可以将其视为二维集。例如，映射符号使用箭头和冒号，

![image](https://user-images.githubusercontent.com/41580525/158836303-55967b79-fffb-4a1d-b65c-0c0c3f94c63f.png)

可以理解为“有一个叫*f*的函数，它以实数作为输入，并将其映射为整数。”在这里，箭头前面的集合称为函数的域（domain），右边的集合称为目标（target）。程序员可能更习惯使用以下等效语言：“有一个名为*f*的函数，它有一个实数参数，并返回一个整数。”换句话说，上面的集合表示法等同于通用编程表示法：

![image](https://user-images.githubusercontent.com/41580525/158837656-819dc649-801c-451a-8ddd-4f587731fd74.png)

所以冒号-箭头符号可以被认为是一种编程语法，就这么简单。点*f*（a）称为a的图像，集合<strong>A</strong>（域的一个子集）的图像是包含A中所有点的图像的目标的一个子集。整个域的图像称为函数的值域（range）。
  (译者注：其实图像的意思就是函数的输出值，*f*（a）是图像，a就是一个输入值，*f*函数定义的时候是左边一个域映射到右边一个目标，即集合<strong>A</strong>在这里是总域的一个区间或者说子集。它作为一个输入，得到的图像是总域作为输入值映射得到的图像（目标）的一个子集，而这个子集其实是由集合<strong>A</strong>中所有的点映射得到的图像（结果）的总和。整个域的图像（目标）其实就是*f*在整个域下能得到的右边目标输出值的值域)
  
[返回目录](#目录) [返回本章开头](#各种各样的数学) [返回本节开头](#集合和映射)
  
### 2.1.1
### 逆映射

如果我们有一个函数![math-20220318](https://user-images.githubusercontent.com/41580525/158928160-8bed2b60-0e04-4207-82b4-eb20a051bf11.png)，那么可能存在一个反函数![math-20220318](https://user-images.githubusercontent.com/41580525/158928236-2de76d69-3ec9-4354-9881-65787b1b4da5.png),它由规则![image](https://user-images.githubusercontent.com/41580525/158920595-f9ea5e5b-9699-4b54-83c4-8b209986710c.png)定义，其中![image](https://user-images.githubusercontent.com/41580525/158920668-be9ee283-9062-4c39-b304-40aea221fc13.png)。反函数的存在需要每个![math-20220318](https://user-images.githubusercontent.com/41580525/158928692-7f68f10b-a689-431c-bdc9-afe6dc6c8950.png)是*f*（即值域等于目标的一个函数）下某点的图像，且只有一个这样的点a能得到![image](https://user-images.githubusercontent.com/41580525/158921479-cddf6b1c-a50f-4f35-bfbe-f5221f30a3f2.png)。这种映射或者函数称为双射。双射将每个![math-20220318](https://user-images.githubusercontent.com/41580525/158928928-30dbdef5-7edc-4cc8-a77d-51fac6f1174d.png)映射到唯一的![math-20220318](https://user-images.githubusercontent.com/41580525/158928692-7f68f10b-a689-431c-bdc9-afe6dc6c8950.png)，同时对每个![math-20220318](https://user-images.githubusercontent.com/41580525/158928692-7f68f10b-a689-431c-bdc9-afe6dc6c8950.png)，只有一个![math-20220318](https://user-images.githubusercontent.com/41580525/158928928-30dbdef5-7edc-4cc8-a77d-51fac6f1174d.png)使得![image](https://user-images.githubusercontent.com/41580525/158923273-6f485350-f0a1-4ca0-8043-a2a74fa9502a.png)（如图2.1）。一组骑手和马之间的双射表示每个人骑一匹马，并且每匹马都被骑着。这两个函数分别是骑手（马）和马（骑手），它们是彼此的反函数。非双射函数没有反函数（图2.2）。

![image](https://user-images.githubusercontent.com/41580525/158924868-b008de90-0336-4d3f-8e3c-16958f2289b4.png)图2.1，一个双射函数*f*和一个反函数![image](https://user-images.githubusercontent.com/41580525/158925076-f4665b02-5884-49ea-ac30-91f805dcf2e9.png).注意到![image](https://user-images.githubusercontent.com/41580525/158925116-21f70aea-e644-4ea0-ab70-da2459e55443.png)其实也是一个双射函数。

![image](https://user-images.githubusercontent.com/41580525/158925306-b0fe5431-999b-4789-9ec6-e24896e59bf2.png)图2.2，函数*g*没有反函数，因为两个![image](https://user-images.githubusercontent.com/41580525/158926097-032925d9-4f84-4135-a213-534281703abf.png)中的元素映射到了![image](https://user-images.githubusercontent.com/41580525/158926154-b1f2d740-a0b2-4ad0-b6f2-74d5c0bcaf39.png)中同一个元素。函数*h*没有反函数，因为![image](https://user-images.githubusercontent.com/41580525/158926211-9d5aa152-fee2-4764-851c-4be6a42a430f.png)中的元素没有任何一个映射到![image](https://user-images.githubusercontent.com/41580525/158926260-ae8f1a8d-b131-4e27-85c2-8a698e384b76.png)中的元素T。

  双射的一个例子是![math-20220318](https://user-images.githubusercontent.com/41580525/158927834-588a9270-b31f-4404-beb9-e6bacd9c0552.png)，![math-20220318](https://user-images.githubusercontent.com/41580525/158930343-b2b78bb5-4f86-4fed-80b0-c0b59dd2d350.png)。那么它的反函数为![math-20220318](https://user-images.githubusercontent.com/41580525/158930477-196286b9-ea68-41e6-b071-52997eee28ad.png)。这个例子表明，标准的表示法可能有些尴尬，因为![math-20220318](https://user-images.githubusercontent.com/41580525/158930674-3f5cbe24-871f-4416-be6d-d877ed8978b9.png)在![math-20220318](https://user-images.githubusercontent.com/41580525/158931031-6bcdaae9-6dca-490e-9a9c-6b3411bab8d3.png)和![math-20220318](https://user-images.githubusercontent.com/41580525/158931101-1bfd241a-ccc4-4012-bfd0-7831bc0f1bf0.png)中都用作虚拟变量。有时候使用不同的虚拟变量更加直观，比如![math-20220318](https://user-images.githubusercontent.com/41580525/158931432-48c0034d-6bb2-47a2-82f2-91237618b904.png)以及![math-20220318](https://user-images.githubusercontent.com/41580525/158931542-cc469561-048d-4c80-943a-9717fb610f84.png)。这会产生更直观的![math-20220318](https://user-images.githubusercontent.com/41580525/158931695-3eb8d6a1-7da0-4a50-99ef-ba6bfb3e8650.png)和![math-20220318](https://user-images.githubusercontent.com/41580525/158931788-6afdf585-422c-47af-bf90-644d33809e5a.png)。一个没有反函数的例子是![math-20220318](https://user-images.githubusercontent.com/41580525/158931944-4b720003-314b-47a5-8d16-2c3330bedd31.png)，那么有![math-20220318](https://user-images.githubusercontent.com/41580525/158932071-198a4b2c-722e-4754-ab95-e701ac5e4729.png)。这里不存在反函数的原因有两个：第一，![math-20220318](https://user-images.githubusercontent.com/41580525/158932410-ec92f172-a8b2-49b7-9cb1-79b9d2ad1f59.png)（即两个不同的元素映射到了目标的同一个元素，不满足双射条件）；第二，没有任何域中的成员能够映射到目标的负数部分（即元素不能全部对应，也不满足双射条件）。请注意，如果我们将域和函数范围限制为![math-20220318](https://user-images.githubusercontent.com/41580525/158932635-aa5e645b-50e3-4ef6-8b6f-c33f586fec82.png),那么![math-20220318](https://user-images.githubusercontent.com/41580525/158932724-92f0e12a-d7d1-45ec-992c-c5c8d96c4ccd.png)就是它的一个有效反函数了。

[返回目录](#目录) [返回本章开头](#各种各样的数学) [返回本大节开头](#集合和映射) [返回本小节开头](#逆映射)

### 2.1.2
### 区间

通常，我们希望指定一个函数处理一个受限的实数，其中一种约束方法是指定区间。例如，一个区间包含介于0和1之间的实数，但却不包含0和1，那么我们可以将其表示为 (0,1)。它因为不包含端点，所以被称为开区间。相应的闭区间（包含其端点）用方括号表示：\[0,1]。这样的符号可以混合使用：例如，\[0,1)表示包含0但是不包含1。在写区间\[a,b]的时候，我们会假定![math-20220318](https://user-images.githubusercontent.com/41580525/158979610-d6b655e5-d44f-4e12-949c-fc050ba04905.png),图2.3显示了表示区间常用的三种方法。同时，我们经常会使用区间的笛卡尔积，例如，要表示点x在三维空间的单位立方体中，我们会将其写成![math-20220318](https://user-images.githubusercontent.com/41580525/158980446-92220841-9ab8-45a5-8ad5-ee5ef779fa94.png)的形式。

  区间与集合运算（交集、并集和差集）结合使用时特别有用，例如，两个区间的交叉部分就是它们共同的点集。符号![math-20220318](https://user-images.githubusercontent.com/41580525/158984140-9c787004-05bc-4b9e-ae08-bf21fd0fcb92.png)用于表示运算交集，例如，![math-20220318](https://user-images.githubusercontent.com/41580525/158984688-a09b2c8f-f7c9-44eb-837d-60f68f2df2f2.png)。对于并集，符号![math-20220318](https://user-images.githubusercontent.com/41580525/158984832-4ce486a9-b821-4647-8ae3-391d3768b7d8.png)用于运算任一区间中共同的点，例如，![math-20220318](https://user-images.githubusercontent.com/41580525/158985751-fa3dd26f-3afc-465a-bfc4-6ba73e10641d.png)。与前两个运算符不同，差运算符根据参数顺序会产生不同的结果。减号用于差运算符，它返回包含在左边区间内而不在右边区间内的数字构成的区间，例如，![math-20220318](https://user-images.githubusercontent.com/41580525/158987375-e4030230-5cfc-4fd9-b220-d689de0e09a1.png)和![math-20220318](https://user-images.githubusercontent.com/41580525/158987496-034735f9-d7a4-44b6-a311-d9da53993660.png)。这些操作特别容易使用区间图（图2.4）来可视化。

![image](https://user-images.githubusercontent.com/41580525/158987775-4c4cebb8-4ff2-4ca0-adcb-a659ec303f60.png)图2.3，表示从a到b的区间的三种等效方法，其中区间包含b但不包含a。

![image](https://user-images.githubusercontent.com/41580525/158988046-9ca06121-1fa8-46f4-9d7c-aaede412a423.png)图2.4，在![math-20220318](https://user-images.githubusercontent.com/41580525/158988221-9e8c00ac-b1df-481b-8fbb-8d41d950784e.png)和![math-20220318](https://user-images.githubusercontent.com/41580525/158988292-0dd7926d-27ba-4063-a95a-a6fc0a0b79e1.png)上进行区间操作。

[返回目录](#目录) [返回本章开头](#各种各样的数学) [返回本大节开头](#集合和映射) [返回本小节开头](#区间)

### 2.1.3
### 对数

虽然现在对数不像以前这么流行，但它们在出现指数项方程的问题中通常很有用。根据定义，每个对数都有一个底数a，x以a为底的对数写作![math-20220318](https://user-images.githubusercontent.com/41580525/158991995-39977e74-362e-4e96-acb4-8df84475d76d.png)，它被定义为获得x需要a自乘的次数，即：

![math-20220318](https://user-images.githubusercontent.com/41580525/158993525-2a37cb83-5545-4474-ae8e-5d10223f8e8b.png)

请注意，以a为底的对数函数和将a提升的指数函数互为反函数，基于这个定义可以得到：

![math-20220318](https://user-images.githubusercontent.com/41580525/158997217-4b168fca-e9fe-4cf1-a1e7-45d705abf403.png)

当我们将微积分应用于对数时，经常会出现特殊数字![math-20220318](https://user-images.githubusercontent.com/41580525/159002858-572eecd7-63ea-4de1-895e-10f78533b5ba.png)。这个以![math-20220318](https://user-images.githubusercontent.com/41580525/158999200-ebc24697-a4f4-4f4b-bfe0-bd6399714ef9.png)为底的对数称为自然对数，我们采用常用的缩写![math-20220318](https://user-images.githubusercontent.com/41580525/158997936-4d8f0581-297c-430a-ad1c-764342d5ed47.png)来表示它：

![math-20220318](https://user-images.githubusercontent.com/41580525/158998851-999988fe-5a6f-4109-b9f8-0721d60ac4cb.png)

请注意，![math-20220318](https://user-images.githubusercontent.com/41580525/158998985-f59899e9-157b-405b-978f-03c759eb3c8a.png)代表“在定义上是等效的”。和![math-20220318](https://user-images.githubusercontent.com/41580525/158999126-27cf8ae6-dada-4c83-9345-cc53ea324dca.png)一样，特殊数字![math-20220318](https://user-images.githubusercontent.com/41580525/158999200-ebc24697-a4f4-4f4b-bfe0-bd6399714ef9.png)也出现在很多的情况下。在许多领域中还会使用一些除了![math-20220318](https://user-images.githubusercontent.com/41580525/158999200-ebc24697-a4f4-4f4b-bfe0-bd6399714ef9.png)以外的特殊底数在它们的式子中来处理和省略底数，即![math-20220318](https://user-images.githubusercontent.com/41580525/159002550-49a5e1da-d211-4d4b-ab6b-c5c6d7203255.png)。例如，天文学家经常使用底数10，理论计算机科学家经常使用底数2。由于计算机图形学借鉴了许多领域的技术，我们将避免这种缩写。

对数函数和指数函数的导数说明了为什么自然对数是“自然的”。
  
 ![math-20220318](https://user-images.githubusercontent.com/41580525/159010967-744b2176-b402-4bf7-ac00-2da32b8d1fc8.png)

当且仅当![math-20220318](https://user-images.githubusercontent.com/41580525/159012147-95a29086-8e11-4846-b8bf-e9dbc5538fef.png)时上述常数乘数是单位的（即此时![math-20220318](https://user-images.githubusercontent.com/41580525/159012312-b91284d4-e996-4341-831a-0eec8f1324e2.png)为常数1）。

[返回目录](#目录) [返回本章开头](#各种各样的数学) [返回本大节开头](#集合和映射) [返回本小节开头](#对数)

## 2.2
## 解二次方程

二次方程的形式为：

![math-20220318](https://user-images.githubusercontent.com/41580525/159018891-95771520-7d12-4804-814b-29a37471a3a2.png)

其中![math-20220318](https://user-images.githubusercontent.com/41580525/159019333-b088b81c-122e-491e-821e-517571b4d9c4.png)是一个实数未知量，而![math-20220318](https://user-images.githubusercontent.com/41580525/159019403-b23be597-a4e8-40ac-b37d-cb82fc491332.png)，![math-20220318](https://user-images.githubusercontent.com/41580525/159019477-0cc2693a-1492-4817-870c-f83f94c75a37.png)和![math-20220318](https://user-images.githubusercontent.com/41580525/159019539-56dd8c78-d244-4bef-bc34-c08ba07eedb1.png)是已知常数。如果你想象一个二维的xy平面图，上面画着![math-20220318](https://user-images.githubusercontent.com/41580525/159019923-605fc131-cc70-4489-8d35-dcd76109d1bd.png)，那么它的解就是函数图像与![math-20220318](https://user-images.githubusercontent.com/41580525/159022005-773562e9-1803-4239-b303-017a1faa61f3.png)处的“交叉点”。因为![math-20220318](https://user-images.githubusercontent.com/41580525/159020191-9f319740-804f-4c98-b66f-7127e278d21a.png)是一条抛物线，根据抛物线的位置（图2.5），将有零、一或两个实数解，这取决于抛物线是否偏离、擦过或击中x轴。

![image](https://user-images.githubusercontent.com/41580525/159022722-fab515e1-4650-4ca0-b8fc-d5a5071788c7.png)图2.5，二次方程根的几何解释是抛物线与x轴的交点。

为了解析如何解二次元方程，我们首先除以![math-20220318](https://user-images.githubusercontent.com/41580525/159023773-33847565-36ac-4ab5-aeb8-42fa51c6b156.png):

![math-20220318](https://user-images.githubusercontent.com/41580525/159023939-69292982-daf1-4897-8a8c-01091bee2dab.png)

然后，我们用“完全平方”将它们配对：

![math-20220318](https://user-images.githubusercontent.com/41580525/159024543-d990ea02-8208-4e01-98b6-4dd109e9ea00.png)

将常数部分移到右边，并开平方：

![math-20220318](https://user-images.githubusercontent.com/41580525/159025164-9c668423-5f4d-4b60-a7ea-b266151f1196.png)

两边同时减去![math-20220318](https://user-images.githubusercontent.com/41580525/159025454-958a2b6d-828b-4434-b8df-c2a187413528.png)并用分母![math-20220318](https://user-images.githubusercontent.com/41580525/159025553-5595ad43-d577-4dbe-a197-d7123671b179.png)构造了一个熟悉的形式：

![math-20220318](https://user-images.githubusercontent.com/41580525/159025871-77e8ff8b-156d-43fb-8ffe-4c3db769b45e.png)（2.1）一个更好的实现是使用等价的表达式![math-20220318 (1)](https://user-images.githubusercontent.com/41580525/159026585-5fc47759-c21f-4441-be5f-beb8995332f5.png)来计算其中一个根，具体取决于![math-20220318 (2)](https://user-images.githubusercontent.com/41580525/159026701-1c8698a6-8be6-4527-a98d-c1d68a7ddbe5.png)的符号（练习7）。

“![math-20220318](https://user-images.githubusercontent.com/41580525/159028155-a09951a5-f18f-4b79-9aa1-011983f7885b.png)”符号意味着这里有两个解，一个是加号，一个是减号，如3±1等于 “二或四”。请注意，决定实数解数量的项是：

![math-20220318](https://user-images.githubusercontent.com/41580525/159028355-ea588bf5-9554-4cf6-832c-c7f6f0bc8e60.png)

这就是二次方程的判别式，如果![math-20220318](https://user-images.githubusercontent.com/41580525/159029584-11fc1b06-c5c3-4c56-8e58-3e193bdc0b3a.png)，则有两个实数解（也称为根）；如果![math-20220318 (1)](https://user-images.githubusercontent.com/41580525/159029692-68948898-6443-4a6c-9484-bcd04f95facd.png)，则有一个实数解（“二重根”）。如果![math-20220318](https://user-images.githubusercontent.com/41580525/159029862-8120b31b-8cc2-4677-8b47-4a4cc6145118.png)，那就没有实数解。

  例如，![math-20220318](https://user-images.githubusercontent.com/41580525/159030522-ef57dd06-42de-4bc3-bedc-2f05d1a1e1dd.png)的根是![math-20220318 (1)](https://user-images.githubusercontent.com/41580525/159030630-5dce34a6-e6a1-4de6-81da-525c209a9108.png)和![math-20220318](https://user-images.githubusercontent.com/41580525/159030661-3425d091-4aa8-428f-921c-b500d86bd571.png)，方程![math-20220318 (1)](https://user-images.githubusercontent.com/41580525/159030736-f5497b16-f8f1-4beb-9f8e-00e3a29f99b1.png)没有实数解，这些方程的判别式分别为![math-20220318](https://user-images.githubusercontent.com/41580525/159031040-8bb8298c-3166-407c-8dfe-94541c856a10.png)和![math-20220318 (1)](https://user-images.githubusercontent.com/41580525/159031076-266e00df-3770-4352-953f-280dff3cf05f.png)，所以我们可以预判解的个数。在程序中，通常最好先计算![math-20220318](https://user-images.githubusercontent.com/41580525/159031238-da70a8e0-2842-4d84-9bcd-12f2245c35ba.png)，如果![math-20220318](https://user-images.githubusercontent.com/41580525/159031238-da70a8e0-2842-4d84-9bcd-12f2245c35ba.png)为负，则返回“无根”，而不取平方根。

[返回目录](#目录) [返回本章开头](#各种各样的数学) [返回本节开头](#解二次元方程)

## 2.3
## 三角学

在图形学中，我们在许多情况下会使用基本的三角学。通常情况下，它并不会太花哨，而我们去记住它的基本定义就会对学习图形学有所帮助。

### 2.3.1
### 角度

虽然我们认为角度就是理所当然的存在，但我们应该回到它们的定义上来，这样我们就可以把角度的概念推广到球体上。两条半直线（源自原点的无限射线）或方向之间形成一个角度，那么必须要有一些惯例来决定它们之间所呈角度的两种可能性，如图2.6所示。角度由其在单位圆上切出的弧段长度定义，一个常见的惯例是使用较小的弧长，角度的符号由指定的两条半直线顺序决定。按照这个惯例，所有角度都会被限制在![math-20220319](https://user-images.githubusercontent.com/41580525/159102802-0b83d2f2-212a-40e3-ab04-02d859699c2e.png)

![image](https://user-images.githubusercontent.com/41580525/159103575-27725ca5-85e2-4158-bdf8-58134e644205.png)图2.6，两条半直线将单位圆切割成两个圆弧，任一圆弧的长度都是两条半直线之间的有效角度。我们可以采用较小的长度为角度的惯例，或者两条半直线按顺序指定，以确定角度![math-20220319](https://user-images.githubusercontent.com/41580525/159103684-4e068797-2fcf-4e5f-932a-df99fcf6875e.png)的弧是从第一条半直线到第二条半直线逆时针扫出的弧。

  这些角度中的每一个都是被两个方向“切割”的单位圆弧的长度，因为单位圆的周长是![math-20220319](https://user-images.githubusercontent.com/41580525/159103017-63513e19-eecb-4aed-af86-13e6c25afb3f.png)，所以两个可能的角度之和为![math-20220319](https://user-images.githubusercontent.com/41580525/159103017-63513e19-eecb-4aed-af86-13e6c25afb3f.png)。这些弧长的单位是弧度，另一个常用单位是度，其中圆的周长为![math-20220319](https://user-images.githubusercontent.com/41580525/159103088-6a055277-0947-465d-9014-8ecca72ca5fd.png)。因此，弧度![math-20220319](https://user-images.githubusercontent.com/41580525/159103113-9a8dcbb0-19f5-48d0-be10-465c0812f668.png)表示的角度为![math-20220319](https://user-images.githubusercontent.com/41580525/159103134-682dcc67-f391-4c1c-a9b8-fdd6b077ef8b.png)。度（degree）和弧度（radian）之间的转换是：
  
![math-20220319 (1)](https://user-images.githubusercontent.com/41580525/159103539-955ba5cb-5d06-450c-9033-1e83283c3818.png)

[返回目录](#目录) [返回本章开头](#各种各样的数学) [返回本大节开头](#三角学) [返回本小节开头](#角度)

### 2.3.2
### 三角函数

给定一个边长为![math-20220319](https://user-images.githubusercontent.com/41580525/159103870-593830ba-688c-4ad1-a3ab-f7aa44e00da4.png),![math-20220319](https://user-images.githubusercontent.com/41580525/159103875-99629375-d804-4815-91c6-c736b007d145.png)和![math-20220319 (1)](https://user-images.githubusercontent.com/41580525/159103883-27daf7fc-5ed1-48b5-9adc-1e6406e2ab19.png)的直角三角形，其中![math-20220319 (1)](https://user-images.githubusercontent.com/41580525/159103891-0dffa38b-29a5-47ae-8f9e-0841c02f2da9.png)是勾股定理描述的最长边（总是与直角相对）或者说斜边，它有如下这一重要关系：

![math-20220319](https://user-images.githubusercontent.com/41580525/159103961-c5eb72d7-6884-4be8-ac97-d4f230df8f27.png)

![image](https://user-images.githubusercontent.com/41580525/159103976-335fee35-a6f4-4dbb-8f67-bfbf1375bd63.png)图2.7，勾股定理的几何证明。

你可以从图2.7中看到这一点，其中大正方形的面积为![math-20220319](https://user-images.githubusercontent.com/41580525/159104123-ac3cc538-1774-4da8-8336-741c52d71481.png)，四个三角形总共面积为![math-20220319](https://user-images.githubusercontent.com/41580525/159104144-527f3ec2-44a4-4910-9db9-a292448278ea.png)，中心正方形的面积为![math-20220319](https://user-images.githubusercontent.com/41580525/159104160-6cb74626-e70d-4600-80e1-d89f34ab5924.png)。

  因为三角形和中心正方形均匀地细分了较大的正方形，所以我们有![math-20220319](https://user-images.githubusercontent.com/41580525/159104234-311f721a-b1ae-4933-bce2-6a27e9b5dee1.png)，由它很容易就能得到上面式子的形式。
  
我们定义了![math-20220319 (1)](https://user-images.githubusercontent.com/41580525/159104276-3194c162-6407-4588-b925-186f688349f9.png)的正弦和余弦，以及其它基于比率的三角表达式：

![math-20220319](https://user-images.githubusercontent.com/41580525/159123187-25c509aa-8723-4a93-b188-b3c1feb020e0.png)

  这些定义允许我们设置极坐标，其中一个点被编码为距原点的距离和相对于正![math-20220319](https://user-images.githubusercontent.com/41580525/159104477-36cbad40-87e3-494d-8529-1d741e8397e4.png)轴的有符号角度（图2.8）。注意到角度![math-20220319 (1)](https://user-images.githubusercontent.com/41580525/159104495-a59df383-bae2-42ee-8f32-fbcacd10a083.png)在惯例中范围为![math-20220319](https://user-images.githubusercontent.com/41580525/159104563-c04c14bd-0b57-4e54-a160-f237e20354ef.png)，且正角度与正![math-20220319](https://user-images.githubusercontent.com/41580525/159104477-36cbad40-87e3-494d-8529-1d741e8397e4.png)轴成逆时针方向，也就是说往逆时针方向旋转的角度为正。这种逆时针映射为正数的约定是主观的，但是它在图形学中许多情况都是如此，因此值得我们记住。

![image](https://user-images.githubusercontent.com/41580525/159104715-d3b5b882-9906-4761-9524-96455bdfb369.png)图2.8，点![math-20220319 (1)](https://user-images.githubusercontent.com/41580525/159104797-d68162b6-0c37-4cc2-9e23-aa93e245a57e.png)的极坐标为![math-20220319](https://user-images.githubusercontent.com/41580525/159104829-0f777e19-2163-43c7-88f0-4c026e70765e.png)。

  三角函数是周期函数，可以以任何角度作为参数，例如，![math-20220319 (1)](https://user-images.githubusercontent.com/41580525/159104890-a6dfe7c8-50a1-4484-901e-0395f4b9cf92.png)。这意味着，当在域![math-20220319](https://user-images.githubusercontent.com/41580525/159104921-3dd8e664-a30f-4490-9eea-4f4d75650e94.png)上考虑的时候，函数是不可逆的，而通过限制标准反函数的值域，可以避免这个问题，这在几乎所有现代数学库（例如，Plauger（1991））中都是以标准方式实现的，这里限制的反函数的定义域和其值域是：
  
![math-20220319 (1)](https://user-images.githubusercontent.com/41580525/159105199-68d52ccf-b7f8-4bbe-be63-277bb098e65f.png)（2.2）

最后一个函数![math-20220319](https://user-images.githubusercontent.com/41580525/159105291-54e97da9-e391-486a-8f13-37f858ef0549.png)通常非常有用，它取一个与![math-20220319 (1)](https://user-images.githubusercontent.com/41580525/159105315-330451c2-caa6-4e78-bde0-c5ad322e7586.png)成比例的![math-20220319](https://user-images.githubusercontent.com/41580525/159105324-247bdd2e-0cd1-4c1a-81a2-ee2d3e30432a.png)值和一个按照相同比例缩放![math-20220319 (1)](https://user-images.githubusercontent.com/41580525/159105360-98cd8aaf-73c2-4b9e-b720-d36117584c7b.png)的![math-20220319](https://user-images.githubusercontent.com/41580525/159105518-69fe6b7e-d47d-4459-9453-b887700fc7bf.png)值并且返回![math-20220319](https://user-images.githubusercontent.com/41580525/159105538-b2ed7bed-2420-4dd9-a0c0-2dcc5047f0b2.png)，该比例系数假定为正。此函数的一种用途是，返回极坐标系中二维笛卡尔点![math-20220319 (1)](https://user-images.githubusercontent.com/41580525/159105585-7d252830-95fb-4e7b-831f-0c587354ed93.png)的角度（图2.9）。

![image](https://user-images.githubusercontent.com/41580525/159105605-5f67d522-15ce-42be-bfc1-bec77cfe0588.png)图2.9，函数![math-20220319](https://user-images.githubusercontent.com/41580525/159105646-3d451824-00b7-4b3e-88d2-b01aaa1a8f04.png)返回了角度![math-20220319 (1)](https://user-images.githubusercontent.com/41580525/159105660-03415225-4ae7-4a0a-9ae5-3affec36e683.png)，这在图形学中通常非常有用。

[返回目录](#目录) [返回本章开头](#各种各样的数学) [返回本大节开头](#三角学) [返回本小节开头](#三角函数)

### 2.3.3
### 有用的恒等式

本章列出了各种有用的三角恒等式，无需推导。

<strong>变换恒等式（Shifting identities）：</strong>

![math-20220319](https://user-images.githubusercontent.com/41580525/159123620-083e8e75-db21-4120-911d-e25e11176a55.png)

<strong>勾股恒等式（Pythagorean identities）：</strong>

![math-20220319 (1)](https://user-images.githubusercontent.com/41580525/159123728-d5d17435-a398-479a-9b7e-58d30461bcc7.png)

<strong>两角和差恒等式（Addition and subtraction identities）：</strong>

![math-20220319](https://user-images.githubusercontent.com/41580525/159124010-a2763908-e3aa-4193-b61f-f993e585520f.png)

<strong>半角恒等式（Half-angle identities）：</strong>

![math-20220319](https://user-images.githubusercontent.com/41580525/159124086-eefb01e5-cb88-4832-b871-14d884382aac.png)

<strong>积化和差恒等式（Product identities）：</strong>

![math-20220319 (1)](https://user-images.githubusercontent.com/41580525/159124293-2625fb8b-8dd6-4d5e-9947-4fa2b15817fb.png)

以下恒等式适用于边长为![math-20220319](https://user-images.githubusercontent.com/41580525/159124367-d94cc212-d1fa-4ce9-9810-757ab8d0321a.png)，![math-20220319](https://user-images.githubusercontent.com/41580525/159124386-29e03c87-6bf1-491f-92f8-e1e126a5b811.png)和![math-20220319 (1)](https://user-images.githubusercontent.com/41580525/159124400-7625ab7d-20c4-4b42-8957-93c7cba91eba.png)的任意三角形，而三角形的角度分别由![math-20220319](https://user-images.githubusercontent.com/41580525/159124421-d2088c54-b293-4b8c-bcad-b3aa7cfe882c.png)，![math-20220319 (1)](https://user-images.githubusercontent.com/41580525/159124433-59b24ec3-2e1b-46fd-a9b4-56f9a48efa4f.png)和![math-20220319](https://user-images.githubusercontent.com/41580525/159124475-b34d755b-0313-4f02-854f-bc5dd14ff789.png)给出（如图2.10）。

![image](https://user-images.githubusercontent.com/41580525/159124532-0912064f-798b-4972-9181-77e3bce5ab2f.png)图2.10，三角定律的几何图形。![math-20220319](https://user-images.githubusercontent.com/41580525/159124827-cca13d5a-fcbb-473a-8539-0d17a7144289.png)

三角形的面积（Triangle area）也可以用这些边长来计算：

![math-20220319 (1)](https://user-images.githubusercontent.com/41580525/159124903-89bb955e-4fb5-447b-a260-d8228d809afb.png)

[返回目录](#目录) [返回本章开头](#各种各样的数学) [返回本大节开头](#三角学) [返回本小节开头](#有用的恒等式)

### 2.3.4
### 立体角与球面三角学

本大节中的传统三角学涉及的都是平面上的三角形，而三角形也可以定义在非平面表面上，这在许多领域都会出现，例如在天文学中，会出现单位半径球面上的三角形。这些球面三角形的边是球面上大圆（单位半径圆）的一部分，对这些三角形的研究涵盖在一个叫做球面三角学的领域，在图形学中并不常用，但有时，当它出现时，它是至关重要的。我们在这里不讨论它的细节，但希望读者知道，当这些问题确实出现时，有这样一个领域的存在，其中有很多有用的定理，比如余弦球面定理和正弦球面定理。有关所使用的的球面三角学原理的示例，请参考关于采样三角形灯光（投影到球面三角形）的论文（Arvo，1995b）。

对于计算机图形学来说，更重要的是立体角。角度可以让我们量化一些东西，比如说“在我的视野中，这两根柱子的距离是多少”，而立体角可以让我们量化一些别的东西，比如“那架飞机覆盖了我多少视野”。对于传统角度，我们将柱子投影到单位圆上，并在单位圆上测量柱子之间的弧长。我们经常使用角度，以至于我们中的许多人都会忘记这个定义，因为对我们来说，它是如此的直观。立体角同样简单，但它们可能看起来更令人困惑，因为我们大多数人都是在成年以后学习它们的。对于立体角，我们投射“看到”飞机的可见方向，并将其投射到单位球体上，然后测量面积。这个区域的面积是立体角，就像弧长是角度一样。角度以弧度（radian）为单位测量，总和为![math-20220319](https://user-images.githubusercontent.com/41580525/159125631-f309347a-1cf7-4e42-9208-284ce8fc5232.png)（单位圆的总长度），而立体角以立体弧度（steradian）为单位测量，总和为![math-20220319](https://user-images.githubusercontent.com/41580525/159125756-76631234-8343-4d93-92d8-851983047b74.png)（单位球体的总面积）。

[返回目录](#目录) [返回本章开头](#各种各样的数学) [返回本大节开头](#三角学) [返回本小节开头](#立体角与球面三角学)

## 2.4
## 向量

向量描述长度和方向，它可用箭头表示。如果两个向量的长度和方向相同，即使我们认为它们处于不同的地方，它们也是相等的（图2.11）。你应该尽可能地把向量看作一个箭头，而不是坐标或者数字。在某些情况下，我们必须在程序中用数字表示向量，但即使在代码中是这样，它们也应该作为对象（objects）来处理，只有低级向量操作才应该关注它们的数字描述（DeRose，1989）。向量将用粗体字符表示，例如![math-20220319 (1)](https://user-images.githubusercontent.com/41580525/159126187-196e0515-0d35-4405-9dad-a4688ab78bd3.png)，一个向量的长度用![math-20220319](https://user-images.githubusercontent.com/41580525/159126258-e72d8fa3-8e26-4206-92d2-73825c06cb03.png)表示。单位向量是长度为一的任意向量。零向量是长度为零的向量，且零向量的方向未定义。

  向量可以用来描述许多不同的事物，例如，它们可以用于存储偏移（offset），也称为位移（displacement）。如果我们知道“宝藏埋在秘密会面地点以东两步和以北三步的地方”，那么我们就知道了偏移量，但不知道从哪里开始。向量也可以用来存储方位（location），也就是位置（position）或点（point）的另一个词。位置可以表示为相对另一个位置的偏移，通常，有一些被理解为原点的位置，此外的所有其他位置都存储为偏移。请注意，位置不是向量。正如我们将要讨论的，你可以将两个向量相加，然而，在计算一个位置的加权平均数时，将两个位置相加通常没有意义，除非这是一个中间操作（Goldman，1985）。将两个偏移相加是有意义的，所以这就是偏移是向量的原因之一，但这也强调了位置并不是偏移；它是相对于特定原点位置的偏移，偏移本身并不是位置。

### 2.4.1
### 向量操作

向量有与实数类似的大多数常用算术运算。只有当两个向量的长度方向相同时，它们才相等。根据平行四边形法则将两个向量相加。该法则规定，两个向量之和是通过将任一向量的尾部与另一个向量的头部靠紧放置而得到的（图2.12）。

![image](https://user-images.githubusercontent.com/41580525/159144775-ad35ef4c-61e8-49a0-b593-20a921230949.png)图2.12，两个向量是通过首尾相连的方式相加，相加的顺序可以任意变换。

两个向量的和向量与原来的两个向量组成了一个“完整三角形”。平行四边形是按任意顺序求和而形成的，这强调了向量的加法是可变换的。

![math-20220320](https://user-images.githubusercontent.com/41580525/159145066-8a0c4c14-f509-46a4-a7ff-a19eff126ea2.png)

请注意，平行四边形法则只是形式化了我们对位移的直觉。想象一下沿着一个向量走，从尾巴到头部，然后沿着另一个向量走，结果的净位移就是平行四边形的对角线。我们还可以为向量创建一元减操作符：![math-20220320 (1)](https://user-images.githubusercontent.com/41580525/159145075-cc616458-458c-4973-8661-6a7403ac37b6.png)（图2.13）是一个与向量![math-20220320](https://user-images.githubusercontent.com/41580525/159145109-e8c11cac-1619-4103-bb9c-11800c67c475.png)长度相同但方向相反的向量，这也允许我们定义一些减法：

![math-20220320 (1)](https://user-images.githubusercontent.com/41580525/159145141-535e7583-bfe7-4823-ab1d-cbf569215f04.png)

你可以用平行四边形可视化向量减法（图2.14），于是我们可以写出：

![math-20220320](https://user-images.githubusercontent.com/41580525/159145185-4f46499b-ea0b-4f75-be6a-7e557e77c53b.png)

![image](https://user-images.githubusercontent.com/41580525/159145236-11647566-462e-4264-ba74-f9ad1558d806.png)图2.14，向量减法其实就是向量加法，只是第二个参数正好相反。

向量也可以相乘。事实上，有几种乘法涉及向量。首先，我们可以通过将向量乘以实数![math-20220320 (1)](https://user-images.githubusercontent.com/41580525/159145274-643a65c7-a1be-4e60-a3d8-2c9dfd91161b.png)来缩放向量。这只是乘以向量的长度，而不改变其方向。例如，![math-20220320](https://user-images.githubusercontent.com/41580525/159145325-c0954813-2610-449f-aac1-02e26b69f5c2.png)是一个与![math-20220320 (1)](https://user-images.githubusercontent.com/41580525/159145338-ec095850-d54d-410e-91b0-45fc0a6bd467.png)方向相同的向量，但是它是![math-20220320 (1)](https://user-images.githubusercontent.com/41580525/159145338-ec095850-d54d-410e-91b0-45fc0a6bd467.png)的3.5倍长。我们将在本节后面讨论涉及两个向量的乘积、点积和叉积，以及涉及三个向量的乘积和行列式，具体见第六章。

[返回目录](#目录) [返回本章开头](#各种各样的数学) [返回本大节开头](#向量) [返回本小节开头](#向量操作)

### 2.4.2
### 向量的笛卡尔坐标

二维向量可以写成任意两个不平行的非零向量的组合，这两个向量的这种性质称为线性独立性。两个线性独立的向量构成二维基，因此这些向量被称为基向量。例如，向量![math-20220320](https://user-images.githubusercontent.com/41580525/159145688-5599addd-a224-4b62-bf0a-01c43b11b27d.png)可以表示为两个基向量![math-20220320](https://user-images.githubusercontent.com/41580525/159145749-a45889d7-7b9f-4580-b241-5460db09ba6c.png)和![math-20220320 (1)](https://user-images.githubusercontent.com/41580525/159145759-c6c46bd5-ac2d-407c-bcd5-457726fc4854.png)的组合（图2.15）：

![math-20220320](https://user-images.githubusercontent.com/41580525/159145800-54e64452-4bc6-474a-92eb-943f88cce7de.png)

![image](https://user-images.githubusercontent.com/41580525/159145818-4c083ea0-741e-4bab-8dab-e8ec0ab3aac4.png)图2.15，任意二维向量![math-20220320 (1)](https://user-images.githubusercontent.com/41580525/159145841-120fabd1-08d7-42b1-846e-c80157fd24f6.png)是任意两个非平行二维向量![math-20220320](https://user-images.githubusercontent.com/41580525/159145848-c1e420b7-2a8f-4cb1-92e1-bcd0c498d2aa.png)和![math-20220320](https://user-images.githubusercontent.com/41580525/159145853-ee33dfdb-d7da-4451-9aa3-f8308e18ed30.png)的加权和。

请注意，权重![math-20220320 (1)](https://user-images.githubusercontent.com/41580525/159145866-ddf8a5a3-30ce-40e1-8710-05f615be8d49.png)和![math-20220320](https://user-images.githubusercontent.com/41580525/159145878-84181d8f-f609-4356-a800-a7f8551f26cc.png)是唯一的。如果两个向量是正交的，那么以它们为基非常有用，即它们彼此成直角。在它们是正交的情况下，如果它们刚好也是单位向量，则更有用。如果我们假设已知两个这样的“特殊”向量![math-20220320 (1)](https://user-images.githubusercontent.com/41580525/159145984-d64deb3c-8830-4ca4-98ed-0c1a40a851d1.png)和![math-20220320](https://user-images.githubusercontent.com/41580525/159145991-1faed3a2-b7f4-4ded-b6cd-03c094bb22d5.png)，那么我们可以使用它们来表示笛卡尔坐标系中的所有其他向量，其中每个向量都表示为两个实数，例如，向量![math-20220320](https://user-images.githubusercontent.com/41580525/159146017-c127c3d6-5d07-4b6c-b284-877f538c9ba7.png)可以表示为：

![math-20220320 (1)](https://user-images.githubusercontent.com/41580525/159146036-3286d712-2377-4f84-aee4-1884ca66c168.png)

其中![math-20220320](https://user-images.githubusercontent.com/41580525/159146056-e68c4d61-9ef4-48ee-936c-78d1a0ceeb07.png)和![math-20220320 (1)](https://user-images.githubusercontent.com/41580525/159146060-d87009e6-cb5f-46fd-9f6f-02996d2c6723.png)是二维向量![math-20220320](https://user-images.githubusercontent.com/41580525/159146071-bc9ee538-728f-490e-9035-62b05cdbb75e.png)的真实笛卡尔坐标（图2.16）。请注意，这在概念上与等式（2.3）没有任何不同，而在等式（2.3）中，基向量不是正交向量。但笛卡尔坐标系有几个优点，例如，根据勾股定理可得![math-20220320](https://user-images.githubusercontent.com/41580525/159146158-b7b631c7-aad9-48d3-a1e6-8e95be00f8cc.png)的长度为：

![math-20220320 (1)](https://user-images.githubusercontent.com/41580525/159146186-1f7f0c54-1324-487a-872d-3e0ba7d314aa.png)

![image](https://user-images.githubusercontent.com/41580525/159146199-fd79ebbf-364e-4a03-b5da-4d4d55396d53.png)图2.16，一组向量的二维笛卡尔基。

在笛卡尔坐标系中，计算点积、叉积和向量坐标也很简单，我们将在本书后面的内容看到。

  按照惯例，我们把其中任意向量坐标写成有序对![math-20220320](https://user-images.githubusercontent.com/41580525/159146360-a3d17293-afaa-49ca-97cf-ce1ea3b91792.png)或列矩阵：
  
![math-20220320 (1)](https://user-images.githubusercontent.com/41580525/159146470-c2b12252-9048-49ec-9f05-9b78abcde3f0.png)

我们使用的形式取决于排版的便利性，我们有时候也会将向量写成行矩阵，表示为![math-20220320](https://user-images.githubusercontent.com/41580525/159146495-8aee2313-0235-4804-9941-047f2101bc33.png):

![math-20220320 (1)](https://user-images.githubusercontent.com/41580525/159146509-ebd29185-adde-4d7f-953e-a59ecc9044a2.png)

我们也可以使用笛卡尔坐标表示三维、四维等向量。对于三维的情况，我们还需要使用一个与向量![math-20220320](https://user-images.githubusercontent.com/41580525/159146552-c1971719-8b4b-4176-9e82-581918a72caa.png)和![math-20220320 (1)](https://user-images.githubusercontent.com/41580525/159146562-a9026abc-22bf-4af6-86f9-837565d893bc.png)都正交的基向量![math-20220320](https://user-images.githubusercontent.com/41580525/159146577-ffee6ab1-73bb-4e8f-bd5c-30e71588fa03.png)。

[返回目录](#目录) [返回本章开头](#各种各样的数学) [返回本大节开头](#向量) [返回本小节开头](#向量的笛卡尔坐标)

### 2.4.3
### 点乘

将两个向量相乘的最简单的一种方式是点积。![math-20220320 (1)](https://user-images.githubusercontent.com/41580525/159146723-124223ee-6f05-44ff-9043-e39ccc0723da.png)和![math-20220320](https://user-images.githubusercontent.com/41580525/159146740-2c2ff298-2cfb-44c9-8e62-485f9ab56a31.png)的点积表示为![math-20220320 (1)](https://user-images.githubusercontent.com/41580525/159146773-1ce75c85-b584-4111-8346-216e38fa9326.png),通常称为标量积，因为它返回的是一个标量。点积返回一个与其参数向量的长度和它们之间角度![math-20220320](https://user-images.githubusercontent.com/41580525/159146801-401308f8-02f6-4b04-b1dc-2dac4acfe7f4.png)有关的值（图2.17）：

![math-20220320 (1)](https://user-images.githubusercontent.com/41580525/159146838-9987e38e-0190-474a-92b6-ca5af1b55b90.png)

![image](https://user-images.githubusercontent.com/41580525/159146849-fd735809-1ada-41bf-bb5d-4aa05727d837.png)图2.17，点积与向量的长度和夹角有关，是图形学中最重要的公式之一。

图形程序中最常用的点积是计算两个向量之间的夹角的余弦值。

  点积也可以用来求一个向量到另一个向量的投影。长度![math-20220320 (1)](https://user-images.githubusercontent.com/41580525/159147029-e955ca55-c9db-48d4-90ac-a15dd5b544ed.png)表示一个向量![math-20220320](https://user-images.githubusercontent.com/41580525/159147050-3d5f7589-d001-4f60-b36d-ffc297e81590.png)以直角投影到向量![math-20220320 (1)](https://user-images.githubusercontent.com/41580525/159147062-0508e689-5813-4388-a751-b995016bc5b5.png)上的“影子”长度（图2.18）：
  
![math-20220320](https://user-images.githubusercontent.com/41580525/159147024-4b9a679f-9e0d-4643-91f7-5f5aab7b398a.png)

![image](https://user-images.githubusercontent.com/41580525/159147097-0d694732-749f-4689-b46e-e65f82120d38.png)图2.18，![math-20220320](https://user-images.githubusercontent.com/41580525/159147138-a9f756a0-fee8-49ce-b3d6-650587584bf9.png)在![math-20220320 (1)](https://user-images.githubusercontent.com/41580525/159147145-542721e0-3b73-4529-bc91-5aac0bab16b9.png)上的投影是由等式（2.5）得出的长度。

点积遵循我们在实数运算中熟悉的一些性质：

![math-20220320 (2)](https://user-images.githubusercontent.com/41580525/159147277-e2b91b62-6f16-4080-992b-0f2eaaa1a01c.png)

如果二维向量![math-20220320](https://user-images.githubusercontent.com/41580525/159147299-41540e0b-4e16-47a0-a11d-05663de4f916.png)和![math-20220320 (1)](https://user-images.githubusercontent.com/41580525/159147306-98f88bc4-d55b-450d-b2c0-23668dde59b0.png)用笛卡尔坐标表示，我们可以利用![math-20220320](https://user-images.githubusercontent.com/41580525/159147327-4029399c-3963-412a-9373-fec278014437.png)和![math-20220320 (1)](https://user-images.githubusercontent.com/41580525/159147342-60313d6c-20c3-4ff7-8875-46f2bd8d6d82.png)来推导它们的点积（此处两个向量均为单位正交基向量）：

![math-20220320](https://user-images.githubusercontent.com/41580525/159147441-b2b18f64-b08c-4163-9967-73a468a80194.png)

类似地，对于三维向量我们可以得到：

![math-20220320 (1)](https://user-images.githubusercontent.com/41580525/159147467-88aeb77c-246b-4fe5-ade6-38e2c7882ec7.png)

[返回目录](#目录) [返回本章开头](#各种各样的数学) [返回本大节开头](#向量) [返回本小节开头](#点乘)

### 2.4.4
### 叉乘

叉积![math-20220320](https://user-images.githubusercontent.com/41580525/159161605-f4494bf1-da68-4e95-bb73-2f26d51a875e.png)通常仅用于三维向量；一般化的叉积在章节注释给出的参考文献中进行了讨论。叉积返回一个与叉积的两个参数向量垂直的三维向量，结果的长度与![math-20220320 (1)](https://user-images.githubusercontent.com/41580525/159161668-ec06d042-b658-49cf-9abc-2741d2e56de6.png)有关：

![math-20220320](https://user-images.githubusercontent.com/41580525/159161718-b5857d8d-a6c3-4b8a-b142-163643835fa4.png)

叉积结果的模![math-20220320 (1)](https://user-images.githubusercontent.com/41580525/159161792-3ca6e3b6-b501-4b18-a3f0-98bf9219a268.png)等于向量![math-20220320](https://user-images.githubusercontent.com/41580525/159161819-0d03699b-2190-4c51-93bd-5addb63db830.png)和![math-20220320 (1)](https://user-images.githubusercontent.com/41580525/159161834-ea05bb76-fb1d-4473-b6df-962f384f17ea.png)形成的平行四边形的面积。此外，![math-20220320](https://user-images.githubusercontent.com/41580525/159161878-4855dc16-656f-4a22-9a2c-5d46c12114e5.png)垂直于![math-20220320 (1)](https://user-images.githubusercontent.com/41580525/159161892-cf92fdbd-fa1d-4e16-b4d2-f96506e32368.png)和![math-20220320](https://user-images.githubusercontent.com/41580525/159161900-511b5d61-90b2-40d3-83a2-0c6be3dd02ac.png)（图2.19）。

![image](https://user-images.githubusercontent.com/41580525/159162011-4f8de310-dcec-404b-83b3-e7c1eaa39623.png)图2.19，叉积![math-20220320 (1)](https://user-images.githubusercontent.com/41580525/159162085-1cfac7c7-69f5-4647-890c-adc8bee6de52.png)是垂直于三维向量![math-20220320](https://user-images.githubusercontent.com/41580525/159162098-c5e0042d-8ad1-4f0a-b733-8d3849c796df.png)和![math-20220320 (1)](https://user-images.githubusercontent.com/41580525/159162106-8370c770-8600-4ce0-9428-49c2c206b442.png)的三维向量，其长度等于所示平行四边形的面积。

请注意，对于这样一个向量，只有两个可能的方向。根据定义，x轴、y轴和z轴方向上的向量由下式给出：

![math-20220320](https://user-images.githubusercontent.com/41580525/159162167-8265a1eb-7693-483e-b080-e396b69021c1.png)

我们设定了一个惯例，![math-20220320](https://user-images.githubusercontent.com/41580525/159162260-bb19a761-a564-45a3-b9ed-c1fc73d0162f.png)必须在正负![math-20220320 (2)](https://user-images.githubusercontent.com/41580525/159162489-98f98da8-6943-4acd-8e37-c2cd18c5d117.png)方向。虽然这个做法有点随意，但标准的做法是假定：

![math-20220320 (1)](https://user-images.githubusercontent.com/41580525/159162305-73bd6e6f-859e-4101-85d5-a82c4f5ff32b.png)

三个笛卡尔单位向量的所有可能排列如下：

![math-20220320 (3)](https://user-images.githubusercontent.com/41580525/159162673-11efaebe-6a8e-4183-9cab-f7c6e1ad1e7a.png)

由于![math-20220320](https://user-images.githubusercontent.com/41580525/159162765-6c976e2d-67f2-463d-81be-643ea41946b3.png)的性质，我们知道向量和自身进行叉积得到的就是零向量，所以![math-20220320 (1)](https://user-images.githubusercontent.com/41580525/159162810-ee454a0b-80ed-4303-9ae4-21e6b8b85951.png)，以此类推。注意，叉积是不可交换的，即![math-20220320](https://user-images.githubusercontent.com/41580525/159162865-4993e08b-1dc8-471d-8981-fe2807dfe53a.png)。仔细的读者会注意到，上面的讨论不足以我们对笛卡尔坐标轴的关系做出明确的描述。更具体地说，如果我们把![math-20220320 (1)](https://user-images.githubusercontent.com/41580525/159162941-9fb7caa7-be0d-40e5-bd4c-5d93c4620720.png)和![math-20220320](https://user-images.githubusercontent.com/41580525/159162953-2d84f40e-4c8a-49e2-afcf-e3ab5e5b212d.png)放在人行道上，![math-20220320 (1)](https://user-images.githubusercontent.com/41580525/159162941-9fb7caa7-be0d-40e5-bd4c-5d93c4620720.png)指向东方，![math-20220320](https://user-images.githubusercontent.com/41580525/159162953-2d84f40e-4c8a-49e2-afcf-e3ab5e5b212d.png)指向北方，那么![math-20220320 (1)](https://user-images.githubusercontent.com/41580525/159162977-64122905-7f77-488c-92c2-c79ef2e59aad.png)是指向天空还是地面？通常的惯例是让![math-20220320 (1)](https://user-images.githubusercontent.com/41580525/159162977-64122905-7f77-488c-92c2-c79ef2e59aad.png)指向天空，这就是所谓的右手坐标系。这个名字来自于用右手手掌和手指指向![math-20220320 (1)](https://user-images.githubusercontent.com/41580525/159163074-a0679b37-c297-497d-a870-74ef8fadba3f.png)的正方向，然后向![math-20220320](https://user-images.githubusercontent.com/41580525/159163091-7297afcd-8752-4417-8fc8-7f3d8b16417a.png)方向旋转弯曲手指的记忆模式，向量![math-20220320 (2)](https://user-images.githubusercontent.com/41580525/159163115-447b64c6-1ac0-4cee-8618-6b70a41a8e1d.png)应该与拇指对齐，如图2.20所示。

![image](https://user-images.githubusercontent.com/41580525/159163137-0a489b81-7d28-4bfa-be82-1f35c20ad65b.png)图2.20，叉积的“右手法则”。想象一下，将右手掌心离身体近的部分放在原点处，手指指向![math-20220320](https://user-images.githubusercontent.com/41580525/159163300-bfd8f8d9-8f17-4ce4-b18a-80f0aa4d75b0.png)的箭头处，然后向![math-20220320 (1)](https://user-images.githubusercontent.com/41580525/159163316-e61650e5-bd0b-4021-a5ef-86f70a71453f.png)所在的方向弯曲，那么此时大拇指的方向就是![math-20220320 (2)](https://user-images.githubusercontent.com/41580525/159163331-d8fc93bf-3f94-48a4-b5d7-4b6f79bde248.png)的方向，反之则是![math-20220320](https://user-images.githubusercontent.com/41580525/159163350-92fac28d-c8d5-43d2-bdcb-02eeeecd1675.png)的方向。

叉积有很好的性质：

![math-20220320 (1)](https://user-images.githubusercontent.com/41580525/159163411-122212f7-685b-4a7c-823a-92625e573e7b.png)以及![math-20220320](https://user-images.githubusercontent.com/41580525/159163548-7f695a86-bd4b-4022-8257-d1587029c970.png)

然而，右手法则的一个后果是:

![math-20220320 (1)](https://user-images.githubusercontent.com/41580525/159163563-2fd60356-9ff8-4ed7-8bb7-b647d4b6709f.png)

在笛卡尔坐标系中，我们可以使用显式展开来计算叉积：

![math-20220320 (2)](https://user-images.githubusercontent.com/41580525/159163813-96eb56f0-c3d3-4de6-8de3-bf17b1414e15.png)

所以，以坐标形式可以写为：

![math-20220320](https://user-images.githubusercontent.com/41580525/159163881-aba669db-619e-42bd-bf17-f4054f4a315e.png)

[返回目录](#目录) [返回本章开头](#各种各样的数学) [返回本大节开头](#向量) [返回本小节开头](#叉乘)

### 2.4.5
### 正交基和坐标系

管理坐标系统几乎是任何图形程序的核心任务之一，而其中的关键是管理正交基。任何一对二维向量![math-20220320 (1)](https://user-images.githubusercontent.com/41580525/159164016-160843a6-79b8-4cf7-8140-b1ed7c21ddc5.png)和![math-20220320](https://user-images.githubusercontent.com/41580525/159164027-249b24a0-7c50-4b40-ae36-fbf6cc86f5fb.png)构成正交基，前提是它们是正交（成直角），且各自为单位长度，因此：

![math-20220320 (1)](https://user-images.githubusercontent.com/41580525/159164100-79855980-44c0-4c99-b080-266b84506b2e.png)以及![math-20220320 (2)](https://user-images.githubusercontent.com/41580525/159164127-dcb7d4c9-ed75-41d9-96c4-744a598c34aa.png)

在三维空间中，三个向量![math-20220320](https://user-images.githubusercontent.com/41580525/159164261-74426602-3378-45d9-b214-b18459f9cd3e.png)，![math-20220320 (1)](https://user-images.githubusercontent.com/41580525/159164273-c4508bde-24b2-49c3-8f48-54d4ac927bc9.png)和![math-20220320](https://user-images.githubusercontent.com/41580525/159164286-cd966837-1971-4e9e-8f4a-c33025a9140f.png)构成正交基，如果它们满足：

![math-20220320 (1)](https://user-images.githubusercontent.com/41580525/159164315-87c88294-3237-4fef-a792-daabbbbd0c45.png)以及![math-20220320](https://user-images.githubusercontent.com/41580525/159164349-e5509583-199f-42cf-bf1a-0b61ae46d3bb.png)

这个正交基是由右手法则得到的：

![math-20220320](https://user-images.githubusercontent.com/41580525/159164424-3d4387f8-fa0e-49dd-bbaa-95267ff22675.png)

否则，则是由左手法则得到的。

  请注意，笛卡尔正则正交基只是无限多个可能正交基中的一个。它的特殊之处在于，它和它的隐式原点位置用于程序中的低级表示。因此，向量![math-20220320 (1)](https://user-images.githubusercontent.com/41580525/159164786-3acb42e7-bf12-4f54-9404-e8ba94c7822c.png)，![math-20220320](https://user-images.githubusercontent.com/41580525/159164797-e568aa73-7dc8-4f46-8905-f83c05984ec4.png)和![math-20220320 (1)](https://user-images.githubusercontent.com/41580525/159164813-37322c79-47f2-4398-9fc5-d313c8c5ab28.png)永远不会显式存储，规范原点位置o也不会显式存储。全局模型通常存储在该标准坐标系中，因此经常称为全局坐标系。然而，如果我们想使用另一个坐标系，它包含原点p和正交基向量![math-20220320](https://user-images.githubusercontent.com/41580525/159164939-4cdff06b-b083-42de-b3d2-010a678a8274.png)，![math-20220320 (1)](https://user-images.githubusercontent.com/41580525/159164945-fec26f17-7954-489b-9ac6-f6ba3ac70bb4.png)和![math-20220320 (2)](https://user-images.githubusercontent.com/41580525/159164949-80245bb3-d654-4424-9161-f5af90c99b32.png)，那么我们会显式存储这些向量，这种系统被称为参考系（coordinate frame）。例如，在飞行模拟器中，我们可能希望保持一个坐标系，它的原点位于飞机机头，正交基准与飞机对齐，同时，我们也会拥有主标准坐标系（图2.21），而与特定对象（如飞机）关联的坐标系通常称为局部坐标系。

![image](https://user-images.githubusercontent.com/41580525/159165839-e5c08f9e-19b1-47e2-a2af-991a727eabce.png)图2.21，始终存在原点为o，正交基为![math-20220320](https://user-images.githubusercontent.com/41580525/159166027-dd06682f-3614-4512-af79-258551d1bdb9.png)，![math-20220320 (1)](https://user-images.githubusercontent.com/41580525/159166046-f28e2d31-fd32-4d97-8d19-6b6036877aa6.png)和![math-20220320 (2)](https://user-images.githubusercontent.com/41580525/159166060-5ac5648c-d432-4a35-b2ce-ffcec85316b9.png)的主坐标系或“标准”坐标系。该坐标系通常被定义为与全局模型对齐，因此通常被称为“全局”或“世界”坐标系。其原点和基向量从未被显式存储。所有其它向量的位置都存储在与全局坐标系相关的坐标中，与飞机相关联的坐标系（局部坐标系）显式存储于全局坐标系中。

在低层次上，局部坐标被存储在标准坐标系中。例如，如果向量![math-20220320](https://user-images.githubusercontent.com/41580525/159166406-9c613ff4-b804-49a6-8935-b2543449d5d1.png)的坐标表示为![math-20220320 (1)](https://user-images.githubusercontent.com/41580525/159166485-076701e2-1cb3-42ff-9f7e-fd4d69fe5af5.png),则有:

![math-20220320](https://user-images.githubusercontent.com/41580525/159166568-b4cd6076-d971-41d2-8ea4-c3acd7f70df1.png)

一个局部坐标系的原点p隐式地包含了一个与标准原点的偏移：

![math-20220320](https://user-images.githubusercontent.com/41580525/159166695-88081393-2bab-42ae-9bb1-8fa1fd078d2f.png)

其中![math-20220320 (1)](https://user-images.githubusercontent.com/41580525/159166723-7b439c2d-fa21-4336-be2d-ab84a7dcf4fc.png)是点p在标准坐标系下的坐标。

  注意，如果我们存储一个关于![math-20220320](https://user-images.githubusercontent.com/41580525/159166810-a5e16dca-f007-4d8f-a967-b2c63ecf9ccf.png)-![math-20220320 (1)](https://user-images.githubusercontent.com/41580525/159166812-e3a586e1-5588-4da8-90b1-d76b7fafca7b.png)-![math-20220320 (2)](https://user-images.githubusercontent.com/41580525/159166813-eb699a75-a0ef-4a9c-bda8-bfe4fb86e09b.png)坐标系的向量![math-20220320](https://user-images.githubusercontent.com/41580525/159166848-2df2c9bd-6e2c-4d3e-b88a-83c3862aa054.png)，我们存储一个三元组![math-20220320 (1)](https://user-images.githubusercontent.com/41580525/159166877-3bb6dbbd-e9c4-4641-ac12-33fc2c42b407.png)，那么我们可以将向量![math-20220320](https://user-images.githubusercontent.com/41580525/159166916-4c06be54-18e3-40f6-b71b-7c185eb55a37.png)的几何解释写为：
  
![math-20220320 (1)](https://user-images.githubusercontent.com/41580525/159167101-04de0727-9b2b-415c-8e76-d79e39fa4f41.png)

要获得存储在![math-20220320](https://user-images.githubusercontent.com/41580525/159166810-a5e16dca-f007-4d8f-a967-b2c63ecf9ccf.png)-![math-20220320 (1)](https://user-images.githubusercontent.com/41580525/159166812-e3a586e1-5588-4da8-90b1-d76b7fafca7b.png)-![math-20220320 (2)](https://user-images.githubusercontent.com/41580525/159166813-eb699a75-a0ef-4a9c-bda8-bfe4fb86e09b.png)坐标系中的向量![math-20220320](https://user-images.githubusercontent.com/41580525/159167209-464af392-b15a-4367-be0a-b3917fe93d9a.png)的标准坐标，只需回想一下，![math-20220320](https://user-images.githubusercontent.com/41580525/159166810-a5e16dca-f007-4d8f-a967-b2c63ecf9ccf.png)，![math-20220320 (1)](https://user-images.githubusercontent.com/41580525/159166812-e3a586e1-5588-4da8-90b1-d76b7fafca7b.png)和![math-20220320 (2)](https://user-images.githubusercontent.com/41580525/159166813-eb699a75-a0ef-4a9c-bda8-bfe4fb86e09b.png)本身都已经存储在标准坐标系中，因此在显式计算中，表达式![math-20220320 (1)](https://user-images.githubusercontent.com/41580525/159167326-7e84971f-102b-4782-b2ea-c60289176c14.png)已经在标准坐标系中。为了获得存储在标准坐标系中的向量![math-20220320 (2)](https://user-images.githubusercontent.com/41580525/159167358-09640c7c-afc9-493d-85e0-f6e5266043ce.png)在局部坐标系![math-20220320](https://user-images.githubusercontent.com/41580525/159166810-a5e16dca-f007-4d8f-a967-b2c63ecf9ccf.png)-![math-20220320 (1)](https://user-images.githubusercontent.com/41580525/159166812-e3a586e1-5588-4da8-90b1-d76b7fafca7b.png)-![math-20220320 (2)](https://user-images.githubusercontent.com/41580525/159166813-eb699a75-a0ef-4a9c-bda8-bfe4fb86e09b.png)中的坐标，我们可以使用点积：

![math-20220320](https://user-images.githubusercontent.com/41580525/159167774-dbb2a3b4-1988-4bd2-b363-223f4e96f29c.png)

上式是正确的，因为对于![math-20220320](https://user-images.githubusercontent.com/41580525/159168078-bf23ccf6-da8d-489f-990d-b59e36f77411.png)，![math-20220320 (2)](https://user-images.githubusercontent.com/41580525/159168092-21c469fc-ca76-49d8-8aca-3a53441d121b.png)和![math-20220320](https://user-images.githubusercontent.com/41580525/159168099-a9bfeea0-b39a-407e-aa41-05e546268c74.png)我们可以知道：

![math-20220320 (1)](https://user-images.githubusercontent.com/41580525/159168117-f1726876-c62a-410b-9f3f-a3e6cfcd9d36.png)

我们可以将![math-20220320](https://user-images.githubusercontent.com/41580525/159168182-8a81a807-dfbf-49fe-8e48-63c9640a647f.png)单独拉出来计算：

![math-20220320 (1)](https://user-images.githubusercontent.com/41580525/159168269-78d3084a-c652-47b6-addb-616f7a97638a.png)

有这样的等式是因为![math-20220320](https://user-images.githubusercontent.com/41580525/159168339-a74a7b05-acc4-4ff9-b15f-e586310c05bc.png)，![math-20220320 (1)](https://user-images.githubusercontent.com/41580525/159168353-25a9faae-fdba-403d-86c2-ba59f829db1b.png)和![math-20220320](https://user-images.githubusercontent.com/41580525/159168363-411175b5-4dc5-4894-abd3-1d329a22d1cd.png)是两两正交的。

  在7.2.1节和7.5节讨论了使用矩阵来进行坐标系的转化。

[返回目录](#目录) [返回本章开头](#各种各样的数学) [返回本大节开头](#向量) [返回本小节开头](#正交基和坐标系)

### 2.4.6
### 用单个向量构造一组基

通常我们需要一个与给定向量对齐的正交基。也就是说，给定一个向量![math-20220320](https://user-images.githubusercontent.com/41580525/159169007-a02062d3-ee77-4ca5-b66b-5a5556141709.png)，我们想要一组两两正交的![math-20220320](https://user-images.githubusercontent.com/41580525/159169033-c232efdc-c80b-4af5-9aca-d0f6f3d9893f.png)，![math-20220320 (1)](https://user-images.githubusercontent.com/41580525/159169049-6c8b6da6-903f-49f1-b66e-3c68446ceea1.png)和![math-20220320 (2)](https://user-images.githubusercontent.com/41580525/159169053-f0944d69-df9e-4469-8449-0e8b71dd6722.png)，使得![math-20220320 (2)](https://user-images.githubusercontent.com/41580525/159169059-b690f357-cdbe-44fc-b04c-2ec9b04b3b18.png)指向与![math-20220320](https://user-images.githubusercontent.com/41580525/159169007-a02062d3-ee77-4ca5-b66b-5a5556141709.png)相同的方向（Hughes & Möller，1999），但我们并不会特别关心![math-20220320](https://user-images.githubusercontent.com/41580525/159169187-7805591f-bda2-46aa-a188-ffecf25c250f.png)和![math-20220320 (1)](https://user-images.githubusercontent.com/41580525/159169192-1dc49fb4-b984-48c9-9bc4-115fb00a3502.png)的方向。一个向量不足以确定唯一答案，所以我们需要一个强大的程序，可以找到任何一个可能的基。

  这可以通过使用叉积来实现，如下所示。首先，将![math-20220320 (2)](https://user-images.githubusercontent.com/41580525/159169276-676d4e21-2d9a-4418-8dc3-09b154c2f6cd.png)设为![math-20220320 (2)](https://user-images.githubusercontent.com/41580525/159169293-8c59af71-e0d3-482e-b54e-b92ec90e08c9.png)方向的单位向量：
  
![math-20220320 (3)](https://user-images.githubusercontent.com/41580525/159169334-bd3e301d-5209-4997-8da3-85933318d9f4.png)

然后，选择任何不与![math-20220320 (2)](https://user-images.githubusercontent.com/41580525/159169366-71b1cc33-b112-4a00-ac30-39258b0b7881.png)共线的向量![math-20220320 (3)](https://user-images.githubusercontent.com/41580525/159169393-517872c5-dc20-4e5b-a79d-290b55cc8d82.png)，并使用叉积构建垂直于![math-20220320](https://user-images.githubusercontent.com/41580525/159169412-cb4126ad-cf96-4dcd-85b9-f3e3978d3e2d.png)的单位向量![math-20220320 (1)](https://user-images.githubusercontent.com/41580525/159169444-16d51e1d-833e-4bd3-9b78-b61156363b6c.png)：

![math-20220320 (2)](https://user-images.githubusercontent.com/41580525/159169488-ecfdb184-2f31-47fd-9688-53c5d8c8256d.png)

如果![math-20220320 (1)](https://user-images.githubusercontent.com/41580525/159169705-56304c07-ecb1-4a95-be6f-9acd4cf85f91.png)与![math-20220320](https://user-images.githubusercontent.com/41580525/159169714-006ba8b2-e386-4d16-8b0a-1cb354fe7bfa.png)共线，分母将消失：如果它们几乎共线，结果的精度将很低。要找到一个与![math-20220320](https://user-images.githubusercontent.com/41580525/159169734-4ea808e7-06b7-43ce-8289-c02cef222975.png)完全不同的向量，一个简单的方法是从![math-20220320 (1)](https://user-images.githubusercontent.com/41580525/159169744-83184e04-e9bb-4958-a2f6-ef3acada3846.png)等于![math-20220320](https://user-images.githubusercontent.com/41580525/159169751-10101027-865c-4d3b-b0d1-2578390428af.png)开始，将![math-20220320 (1)](https://user-images.githubusercontent.com/41580525/159169755-07449396-3724-4982-be73-c0b6c8655720.png)模最小的分量改为1。例如，如果![math-20220320 (1)](https://user-images.githubusercontent.com/41580525/159169875-1ac5bdc0-cc52-4a5f-8991-0cfb5e823263.png)，那么![math-20220320 (1)](https://user-images.githubusercontent.com/41580525/159169951-cf4e9e85-47ae-454c-baba-58b211aab3b6.png)。一旦有了![math-20220320](https://user-images.githubusercontent.com/41580525/159169962-04014d80-3e62-4b74-9608-5143e470e65d.png)和![math-20220320 (2)](https://user-images.githubusercontent.com/41580525/159169996-ce28d25b-4df4-4444-81e6-300b1461e0f0.png)在手，那么找到最后一个基向量很简单：

![math-20220320 (3)](https://user-images.githubusercontent.com/41580525/159170038-2fa57e01-aefa-4f8c-977a-186e28ef57ef.png)

![image](https://user-images.githubusercontent.com/41580525/159170569-59cd448f-a99f-4420-aa88-b9180b3f6968.png)

使用这种构造的情况的一个例子是表面着色，其中需要与表面法线对齐的基向量，但其围绕法线怎么旋转通常不重要。

  对于严格的生产代码来说，Pixar的研究人员最近开发了一种相当出色的方法，可以从两个向量构建一个新的向量，其紧凑度和高效率令人印象深刻（Duff等人，2017）。它们提供了经过实战测试的代码，并且我们鼓励读者使用它，因为在整个行业使用它的时候没有出现过“陷阱”。

[返回目录](#目录) [返回本章开头](#各种各样的数学) [返回本大节开头](#向量) [返回本小节开头](#用单个向量构造一组基)

### 2.4.7
### 用两个向量构造一组基

[返回目录](#目录) [返回本章开头](#各种各样的数学) [返回本大节开头](#向量) [返回本小节开头](#用两个向量构造一组基)
