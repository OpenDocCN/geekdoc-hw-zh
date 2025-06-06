# 第十七章：Android 浏览器

要理解 Android 浏览器应用程序，首先需要了解 Android 之前的网络浏览状态。

Google 一直非常关注网络技术。从一开始，Google 的主要任务就是提供搜索查询的结果。因此，广泛投资于像浏览器这样的网络技术是合乎逻辑的；提供结果的工具越好，Google 为这些结果提供的体验就越好。尤其是在 2000 年代初期，浏览器公司所推动的网络浏览状态对 Google 来说至关重要。

## 伟大的浏览器战争

在互联网初期，Netscape 浏览器是当时的王者；桌面用户会下载并使用 Netscape，因为那时就是上网的方式。但是微软推出了自己的浏览器 Internet Explorer（IE），最终将其与 Windows 捆绑在一起。捆绑 IE 几乎保证了微软的浏览器会成为大多数用户的默认浏览器，因为它作为操作系统的一部分预装，而且（当时）足够好。Internet Explorer 甚至在 Apple 推出自己 Safari 浏览器之前，曾是 MacOS 上的默认浏览器，直到 2003 年。

Netscape 和 IE 之间的紧张关系成为了维基百科幽默地（尽管是正确的）称之为“第一次浏览器战争”的核心，这场战争导致了诉讼，并最终使 Netscape 死亡，Internet Explorer^(1) 接管了全球市场。

在此期间，微软实际上处于决定人们如何访问网络的位置，因为 IE 越来越成为他们进入网络的大门。

为了确保所有用户都能访问到出色的网络体验，包括正在引入的新网络技术，Google 开始资助浏览器开发。最初，Google 与 Mozilla 基金会合作，支持 Firefox 浏览器。特别是，Google 通过实施或协助一些改进措施，贡献了工程资源，包括性能提升、内联拼写检查、软件更新系统以及浏览器扩展等。Google 并没有像微软或苹果那样拥有可以捆绑浏览器的操作系统，但它可以提供一个更好的浏览器替代方案，并鼓励人们切换使用。

Google 在 2006 年创建 Chrome 浏览器时决定进一步推动这种方法。它从头开始（使用开源的 WebKit 代码库），构建了一个全新的浏览器，以实现 Google 想让用户体验的网络效果。Google 专注于添加现代化的网络功能，并提高浏览速度。^(2) Google 还默认在 Chrome 中捆绑了对其搜索引擎的访问；在浏览器的地址栏中输入搜索查询会显示 google.com 上的搜索结果，就像用户访问了 Google 的主页并在搜索栏中输入一样。

Chrome 浏览器于 2008 年 9 月推出，并最终获得了不错的市场反响。用户回到了下载浏览器应用程序的世界，而不是仅仅使用随桌面电脑预装的浏览器。

## Android 需要一个浏览器

Android 对移动浏览器的需求与谷歌对桌面浏览器的需求不同。

与桌面浏览器的情况不同，Android 平台是从零开始构建的。他们不需要更好的浏览器；他们需要*任何*浏览器。具体来说，他们需要一个能够让用户在手机上查看网站的应用，就像在桌面电脑上那样。他们还需要一种将网页内容直接集成到其他应用中的方式，因为他们意识到移动应用和网页内容之间的界限正在模糊。

例如，一个移动应用程序可能想要向用户展示来自网站的内容。有时候，直接在应用中展示内容比将用户重定向到浏览器应用程序更好。这样的动态不仅提供了更加流畅的体验，而且确保用户不会永远离开应用程序。而且，许多开发者更熟悉 HTML 和 JavaScript，这些是网络语言，因此为他们提供在移动应用中创建网页内容的方式，扩大了开发者群体，也使人们能够更快地创建基础的 Android 应用程序。

Android 团队创建了 WebView 来满足这一需求。WebView 是一个可以嵌入到更大的 Android 应用中的网页查看器。它与 Android 浏览器一同开发，因为浏览器本质上是一个被额外控制和 UI 包围的 WebView。

但一开始，这些都不存在，平台需要所有这些功能。所以他们需要一个开发者来把这些东西整合起来。幸运的是，他们中的许多人曾与 Danger 公司的一位工程师合作过：黄伟。

## 黄伟和 Android 浏览器

黄伟有多年的开发网页浏览器和软件的经验。但那段经历并不是从童年开始的。

当黄伟十二岁时，他参加了一门编程课程。但二进制数学的原理让他难以理解，他放弃了。当母亲给他展示一篇关于计算机是未来的文章时，黄伟坚信他刚刚毁了自己的一生。

许多年后，在高中时，他再次尝试编程，这一次取得了更多成功。他最终获得了电气工程学位，然后在研究生院爱上了计算机图形学编程。

研究生毕业后，黄伟在微软找到了工作，与其他未来的 Android 团队成员一起工作，包括 Steve Horowitz。黄伟为 WebTV 和 IPTV 产品开发了网页浏览器，学习了在非桌面屏幕上渲染网页内容所需的技术。但最终，他想做些其他的事情。“帮助人们看更多电视似乎并不是一件特别崇高的事情。”

史蒂夫把魏介绍给了 Danger 公司的 Andy Rubin。那时，Danger 还没有转型做手机，他们仍在开发“坚果黄油”数据交换设备，而魏对这个项目并不感兴趣。“我不确定这个设备能否卖得出去。商业模式似乎有些薄弱。所以我决定去 AvantGo。我觉得那里更有可能成功。”

“这不是一个非常明智的决定。”

AvantGo 在魏加入后不久，于 2000 年 9 月进行了首次公开募股（IPO），恰逢互联网泡沫开始破裂之时。AvantGo 像许多其他初创公司一样，遭遇了困境。“我的时机真的很糟糕。我赶上了那个泡沫的末期，然后一切都崩溃了。”此外，工作和文化也不是魏所想要的，因此他开始寻找其他机会。“我联系了 Andy。在风险投资的支持下，他们决定做手机。这听起来更令人兴奋，所以我在 2001 年 1 月加入了 Danger。”

在 Danger，魏再次在做一个网页浏览器。Danger 的手机功能非常有限，因此与浏览器在桌面电脑上运行的方式（或后来在 Android 手机上的运行方式）不同。Danger 在服务器上运行一个*无头*^(3)浏览器。当用户在 Danger 手机上的浏览器应用中打开网页时，页面会在服务器上渲染。服务器然后会重新格式化该页面，并将简化版发送到手机上。这种方法没有为用户提供完整的网页功能，因为缺少网页的动态功能。但他们获得的网页浏览体验，接近他们在桌面电脑上熟悉的体验，远远比他们在其他手机上的体验要丰富。

魏在 Danger 工作了四年，为几款 Danger 的 Hiptop 设备发布了浏览器。最终，他准备迎接新的挑战，希望是另一家初创公司。来自 Danger 的朋友 Chris DeSalvo 建议他去找 Andy Rubin，后者已经离开了 Danger，正在经营一个名为 Android 的隐秘初创公司。魏当天晚上通过即时消息联系了 Andy，Andy 问他是否想加入。

“他说，‘哦，顺便说一下，我们要被 Google 收购了。’”

“我当时有种沉重的感觉，因为我正在寻找一家初创公司。这并不是一家初创公司。我得好好考虑一下。当时我对 Google 并不熟悉。我以为它只是一个搜索公司。我当时并没有完全理解 Google 的雄心壮志。但 Andy 所传达的兴奋感仍然说服我加入了。”

魏于 2005 年 9 月加入了 Google 的 Android 团队，成为第二位加入的收购后员工，仅次于他的朋友 Chris。

魏的第一个项目是……又一个浏览器。但在他能够编写浏览器应用之前，还有很多工作要做，因为作为一个平台，Android 实际上还不存在。“我下载了代码库。我有点惊讶。你们怎么把这家公司卖给 Google，只不过是一些 JavaScript 代码？”

第一个任务是为浏览器选择一个起点。到 Android 开始时，已经有多个开源浏览器引擎可以作为起点，因此 Wei 不必从头编写整个应用程序。WebKit 是基于另一个开源浏览器项目 KHTML，由 Apple 启动，并成为 Apple Safari 浏览器的基础。“我非常喜欢这个代码库，所以对我来说这不需要多想。”

Wei 开始基于 WebKit 引擎构建浏览器。与此同时，浏览器团队也在壮大，首先是管理层：Rich Miner。

## Rich Miner 构建团队

Rich Miner，后来帮助建立了许多 Android 早期的企业合作伙伴关系，他既懂商业又懂技术。他在小学时接触到了编程，当时班级通过打孔卡学习 Fortran。“直到今天，我仍然惊讶于我们应用程序中占用的内存量，我时常想起自己当时如何挤进修改后的代码。”

Rich 在大学一年级时首次展示了他将商业与工程结合的技能。他为自己的 Commodore 64 计算机编写了一款游戏，并在一些朋友的帮助下将其出售。“我和室友们在宿舍里有一套磁带复制系统，自己包装游戏。我会四处走动，亲自将游戏卖给当地的 Commodore 经销商。我还在一本 Commodore 杂志上投放了广告，并通过电子邮件处理订单。”

Rich 曾就读于马萨诸塞大学洛厄尔分校，学习物理学，但很快转了专业。“我坚持了半个学期后意识到我应该学习计算机科学，我的成绩也开始反映出这一点。”

在本科学习期间，Rich 成为学校生产力提升中心的负责人之一，成功为该中心争取到来自 Digital、IBM 和 Apollo 等公司的数百万美元资助。在研究生阶段，他继续在实验室工作，并成为联合主任，同时攻读博士学位。实验室孵化的一个项目促使 Rich 在 1990 年 12 月创办了 Wildfire Communications 公司。Wildfire 提供了包括基于语音的自动助手服务，能够转接电话和留言等功能。Wildfire 经营了近十年，直到被法国电信公司 Orange 收购。收购后，Rich 在剑桥创建了 Orange Labs，并担任研究主任以及新创风险基金的负责人。

在 Orange 工作期间，Rich 帮助推出了第一款 Windows Mobile 手机，并在 Orange 的网络上运行。这次经历并不愉快，因为 Microsoft 对最终设备的控制要求过高。Rich 从这个项目中得出结论，移动生态系统应该是开放的平台，而不是被平台提供商所限制的选择。

Rich Miner 是 Android 的共同创始人，并且是帮助其被收购的商业团队成员。但在加入谷歌后，他开始寻找帮助日益壮大的工程团队的方法。他接受了管理初期浏览器项目的工作。

Rich 在 Android 被收购后留在波士顿地区，远离位于山景城的团队其他成员。谷歌在波士顿市中心只有一个小型的销售办公室，于是 Rich 向谷歌高层 Eric Schmidt（首席执行官）和 Alan Eustace（工程副总裁）游说，希望能在波士顿开设一个工程师办事处。这是一个艰难的推销。“Eric 对东海岸的经历不太好。Sun Microsystems 在他掌舵时曾在这里开设过一个工程办公室，但他们将其设在了城市的边缘。我不得不说服他，靠近大学的地方能够吸引到最优秀的人才。我们可以建立一个伟大的办公室。”

Rich 说服了谷歌高层，谷歌在剑桥市中心开设了一个办公室，就在 MIT 街对面。^(5) Rich 在那里招聘了第一批工程师，其中包括一些 Android 团队的成员。

Rich 招募了他在 Orange Labs 的前同事 Alan Blount 加入浏览器团队。与此同时，在山景城，Wei 为团队找到了另一位工程师：Grace Kloba。几年前，当他在 Adobe 工作时，Wei 曾说服 Grace 放弃她的博士学业并加入他。这次，他再次说服她离开 Adobe。

## Grace Kloba、WebView 和 Android 浏览器

Grace 从母亲那里第一次学会编程，她母亲是中国第一代接受计算机教育的人，时间大约在 1970 年代末。她的母亲从学生迅速转为教师；在参加了一个为期三个月的强化编程课程后，她回到大学负责计算机实验室并教授编程语言课程。在这个过程中，Grace 学到了 BASIC 和 Fortran 编程的一些知识。

Grace 后来根据图像处理实验室的优良设施选择了她的本科专业。这一选择效果很好，帮助她打下了计算机科学和电气工程的基础。大学毕业后，她来到美国斯坦福大学攻读计算机图形学的研究生课程。她在斯坦福的同学中有 Wei，而十年前他们曾在中国一起上学。

Grace 通过了博士资格考试，正在寻找论文题目时，Wei 联系了她，提供了 Adobe 的机会。Grace 离开了研究生院，加入了 Adobe 工作了几年。之后，2006 年，Wei（那时已在谷歌）再次联系了她，Grace 进行面试后收到了谷歌的工作邀请。

Wei 希望 Grace 和他一起加入浏览器团队，但他必须说服 Steve。Android 招募了在嵌入式系统、移动设备和操作系统平台方面有经验的领域专家，而 Grace 并没有这种经验。但 Wei 向 Steve 保证一切都会顺利进行，Grace 于 2006 年 3 月加入了 Android 浏览器团队。^(6)

Grace 需要解决的问题之一是如何在当时手机的小屏幕上更方便地查看网页内容。她有排版文本内容的经验，^(7) 这在她使浏览器能够在小屏幕上以合理的方式显示文本时派上了用场，尽管网页作者在编写原始 HTML 内容时设想的是更大的内容区域。

在她团队的工作期间，她还解决了浏览器和 WebView 组件中的许多其他问题。毕竟，在 Android 初期的几年里，只有少数几个人支持这一大块功能。她实现的一些功能包括多线程支持、改进的网络能力，以及常见的浏览器 UI 元素，如标签页。

还有一个最后时刻的项目，就是为了 2010 年 1 月初 Nexus One 发布，搞定捏合缩放功能的实现。Grace 在假期归来时，发现 Andy Rubin 在问实现这个功能需要多长时间。他非常希望在即将发布的这款手机上看到这个功能，发布会就定在那个月。三周后，Grace 交付了这个功能，手机也带着这项新功能发货了。

## Cary Clark 和浏览器图形

Android 团队大部分成员都集中在山景城。但浏览器团队是一个显著的例外：Grace 在山景城，Wei 在西雅图，Rich 和 Alan 在波士顿。然后，Skia 团队在完成他们的图形引擎工作后，加入了浏览器团队的工作。

浏览器的绘图需求与 Android 系统的其余部分不同。渲染图形是 Skia 团队擅长的工作，因此他们负责渲染浏览器内容。例如，Cary Clark 花了大量时间让原本为桌面计算机设计的网页，在这种新型且受限的设备上能够合理显示和响应。

Cary 在加入 Android 团队之前，已经有了长时间的 2D 图形和浏览器经验。但他的编程背景更早可以追溯到 1968 年，当时他 11 岁，圣诞节收到了一个 Digi-Comp I。这个设备不像我们今天所知的计算机，而是通过塑料和金属部件来执行简单的布尔运算和数学运算，例如从零到七的计数。^(9) Cary 对这个机器非常着迷，以至于把它用坏了，并在第二年圣诞节请求得到同样的礼物。

他在 70 年代末期升级到了一台二手的 Apple II，当时他正在上大学，花了大量时间在宿舍里学习编程，拆解史蒂夫·沃兹尼亚克在 Apple II 上的 BASIC 实现，结果导致他未能顺利完成学业。后来他回到学校，完成了学位，但在此期间他已开始在一家爱好者计算机商店从事销售工作。当顾客对他们的 Apple 计算机有疑问时，Cary 会拨打地区 Apple 技术支持办公室的电话来寻求答案，但他发现工作人员根本不知道设备的实际工作原理。于是他申请并获得了这份工作。作为地区支持部门的一员，他偶尔会打电话到库比蒂诺总部，但他意识到那里的技术支持人员也不了解足够的知识，于是他大声抱怨，最终搬到了库比蒂诺，并在 Apple 总部的技术支持办公室工作。

在 Lisa^(10)和 Mac 的开发过程中，Cary 转向了管理岗位，同时仍然从事编程工作。但最终他决定全职做软件工程师：“我曾是一个糟糕的经理。”他在 Apple 工作直到 1994 年，期间参与了多项工作，其中包括领导 QuickDraw GX^(11)的开发，这是一个新的 2D 图形库，能够比 Mac 原有的 QuickDraw 库更快地绘制图形。这个项目的代号是 Skia，Cary 从一个希腊词中选取了这个名字，该词指的是在墙上绘制影子的动作。QuickDraw GX 的主要功能是绘制轮廓并填充，因此这个代号十分贴切。

Cary 最终离开了 Apple，先后在 WebTV 和被微软收购后的微软工作，他与一些未来的 Android 工程师们合作。Cary 负责 WebTV 浏览器的开发，尝试让原本为桌面计算机设计的内容在电视上合理显示和互动，电视的输入机制完全不同。后来他搬出了硅谷，前往北卡罗来纳州的查佩尔希尔，在那里为微软远程工作。在那里，他开始与 Mike Reed 交流，Mike 是他在 Apple 时认识的。Mike 将 Cary 引入 Openwave，在那里 Cary 再次从事浏览器技术的工作。然后，Mike 离开了 Openwave，创建了一个新的图形创业公司，名为 Skia，以纪念 Cary 为 QuickDraw GX 选择的代号。

当 Cary 开始参与 Android 浏览器的开发时，他面临了一些问题需要解决。例如，输入问题非常复杂，需要解决如何将键盘、方向键、轨迹球以及最终的触摸事件转换为网页上的交互。Mike 说：“第一款拥有触摸屏的设备仍然有轨迹球和箭头键。所以我们不得不在两种世界中兼顾。浏览器上更困难一些，因为有两种方法可以设置当前的关注项和焦点。你可以用手指滑动，也可以按下箭头键多次。所以这造成了一些复杂性。”

其中一个复杂的问题是如何在网页中导航链接。如果用户试图使用 D-pad 导航，需要有一种方法来跳转到“下一个”链接。所以如果用户按下 D-pad 上的右键，焦点需要移动到右侧的下一个链接。但网页并没有相对定位链接的概念，因此根据用户的输入，哪一个链接应该获得焦点并不明显。此外，Cary 还需要设计一种系统来直观地指示某个链接已获得焦点，以便用户知道当他们按下选择按钮时，会点击哪个链接。

流畅滚动是另一个难题。Mike 说：“Apple 设定了每个人都应该流畅滚动的预期。我们在第一版使用轨迹球和箭头时并没有流畅滚动。当我们滚动二十个像素时，屏幕就跳动，就像地球上所有桌面计算机一样。然后突然之间，你必须让一切都流畅滚动，无论它是手指滑动还是其他。那时我们真的下了很大功夫。Cary 发明了^(12) 图片^(13) 对象，这个在 Skia 中之前是没有的，它是一个显示列表。浏览器可以处理所有慢速的 Java 单线程内容，将其交给另一个线程，然后我们可以尽快地绘制图片，而不必与浏览器进行交互。”

另一个任务是如何让现实中的网页在内存有限的小设备上合理显示。Cary 多年前在 WebTV 产品上处理过相关问题，成功地将针对桌面计算机设计的网页显示在电视屏幕上。但他在 Android 浏览器上遇到的问题是全新的：网页上的内容实在是太多了，包括“那些疯狂长的页面，尤其是当它们被适配到手机屏幕宽度时。”

Cary 当时最喜欢的一个例子是 *Wikipedia* 上关于 **奶酪** 的页面，^(14)该页面由于某种原因非常非常长。“它的高度有好几百万像素。我们无法在数学系统中表示这么多像素，因此我们不得不想办法解决这个问题。”

当这个问题解决后，又出现了另一个问题；即使用户最终能够看到页面上的所有内容，滚动整个页面仍然需要很长时间。所以 Cary 在浏览器中实现了一个系统，能够检测到用户是否在反复滚动，并且在页面上弹出一个放大镜对象，显示整个页面的缩略图，用户可以通过它快速跳转到页面中的特定位置。
