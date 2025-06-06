# 前言

![](img/nsp-boxall502581-ct.jpg)

*微控制器*（或简称*MCU*）是一种小型的完整计算机，能够集成在一个单一的集成电路中。就像你的台式计算机一样，微控制器包含一个处理器、内存、接收来自不同来源输入的设备，以及可以用来控制或与外部设备通信的输出端口。

得益于像 Arduino 和 PICAXE 这样的开发平台的成功，微控制器在电子领域以及爱好者和黑客中被越来越广泛地使用。这样的开发平台简化了初学者的项目，但它们可能比较昂贵；它们还将用户与微控制器之间加了一层抽象，降低了微控制器的性能，且通常无法让用户访问其完整的功能集。经验更丰富的用户可能希望直接控制微控制器或在项目中使用更便宜的零件。或者，如果你是初学者，你可能希望在没有人为加诸额外负担的情况下，开始你的微控制器之旅。

这本书正是为此而来。无论你是完全的初学者还是多年的电子爱好者，*AVR 工作坊*将向你展示如何利用来自 Microchip AVR 8 位微控制器系列的两款廉价芯片，这些芯片因 Arduino 及兼容板而广为人知。一旦掌握了这些芯片，你将能够最大化其性能，通过更便宜的硬件创造出强大的项目。在这个过程中，你将学习到电子学、C 语言编程等内容。

我将带领你完成 55 个逐步增加难度的项目，这些项目基于 Microchip 的 ATtiny85 和 ATmega328P-PU 微控制器，我将为每个项目解释并演示你需要了解的一切。你将从闪烁一个小灯开始，接着学会计时、捕捉和分析现实世界的数据（如温度），甚至控制小型电动设备。本书不涉及用于物联网的 AVR，因为那是一个更高级的话题，但完成这些项目后，你将能够利用 AVR 微控制器，掌控各种设备、传感器、电机、显示器等，充分实现你的创意和梦想。

我写这本书是为了广泛的人群。你可能是想在微控制器方面提前学习的学生，可能是没有数字电路或微控制器电路经验的电子爱好者，可能是想提升自己工作知识的员工，或只是一个喜欢制作东西的人。这本书适合任何对学习 AVR 技术并利用它创建自己项目的人。

我的目标是让你在读完这本书后，带着持久的知识和自信继续学习和创作。第一章将通过介绍一些使用 AVR 微控制器的酷炫现实世界项目，帮助你入门，然后向你展示如何设置自己的工作站。
