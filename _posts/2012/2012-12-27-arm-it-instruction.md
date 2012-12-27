---
layout: post
title: ARM IT指令解析
categories:
- ARM汇编
tags:
- ARM
- 汇编
---


===ARM IT指令解析

最近研究iOS程序的反汇编，重新学习了ARM的指令。其中，IT指令着实让我费了点时间，差了一些资料总算明白。特记录于此，防止自己日后忘记。也期望能够帮助其它不理解这个指令的朋友。

RealView的《汇编指南》对IT指令的解析如下：
http://infocenter.arm.com/help/index.jsp?topic=/com.arm.doc.dui0204ic/Chdhcfbc.html
  			
				
	IT (If-Then) 指令由四条后续条件指令（IT 块）句组成。 这些条件可以完全相同，也可以互为逻辑反。
	IT 块中的指令（包括跳转）还必须在语法的 {cond} 部分中指定条件。
	无需在代码中编写 IT 指令，因为汇编器会根据在后续指令中指定的条件为您自动生成这些指令。 不过，如果确实	需要编写 IT 指令，则汇编器会根据后续指令中指定的条件对 IT 中指定的条件进行验证。
	编写 IT 指令可确保您会考虑如何在代码设计中放置条件指令以及选择条件。
	在汇编为 ARM 代码时，汇编器会执行相同的检查，但是不会生成任何 IT 指令。
	
	
	限制
	不允许在 IT 块中使用下面的指令：
	IT
	CBZ 和 CBNZ
	TBB 和 TBH
	CPS、CPSID 和 CPSIE
	SETEND
	使用 IT 块时的其他限制有：
	跳转指令或修改 pc 的任何指令只能是 IT 块中的最后一个指令。
	无法跳转到 IT 块中的任何指令，除非在从异常处理程序返回时。
	不能在 IT 块中使用任何汇编器指令
	
	
举个例子

	if (R4 == R5)
	{
	  R7 = R8 + R9;
	  R7 /= 2;
	}
	else
	{
	  R7 = R10 + R11;
	  R7 *= 2;
	}
汇编如下

	CMP R4, R5
	ITTEE EQ
	ADDEQ R7, R8, R9    ; if R4 = R5, R7 = R8 + R9
	ASREQ R7, R7, #1    ; if R4 = R5, R7 /= 2
	ADDNE R7, R10, R11  ; if R4 != R5, R7 = R10 + R11
	LSLNE R7, R7, #1    ; if R4 != R5, R7 *=2
	
IT语法
	
	语法
	IT{x{y{z}}} {cond}

IT后面最多可以跟4条指令，其中xyz只可以用T或者E，T就是Then，条件为真时执行，E是Else，条件为假时执行。
ITT后面就是两条指令，ITTEE就是四条指令。
