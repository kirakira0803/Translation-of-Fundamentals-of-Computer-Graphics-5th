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



[返回目录](#目录) [返回本章开头](#各种各样的数学) [返回本大节开头](#集合和映射) [返回本小节开头](#区间)















