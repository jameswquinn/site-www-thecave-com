---
layout: post
title: 'To Data Bind or Not To Data Bind?  That is the Question.'
categories:
  - blogger

---

I had a lengthy discussion with another developer today regarding data binding in .NET.&nbsp; I started thinking about this more after the conversation ended and I realized there are some who think data binding should always be used in Windows based .NET applications.&nbsp; The conversation today brought back memories of how developers overused data binding when VB 3.0 was released into the wild.
<br />
<br />Data binding in .NET is a vast improvement over past attempts at providing a data binding feature in a programming language.&nbsp; I for one love the fact that I can data bind to different data structures and that I am not limited to binding to ADO.NET datasets only.&nbsp; I often use data binding in my ASP.NET applications that use a repeater.&nbsp; This feature alone has helped me build web pages faster, but I do not believe data binding is the silver bullet for all cases of moving data between structure and presentation.
<br />
<br />Consider a case where you are developing a Windows application and the presentation tier works with custom data structures only, no dataset.&nbsp; The window must allow the user to edit values stored within the data structure.&nbsp; One easy way to do this is to bind the data structure to the window elements.&nbsp; Changes in the data will immediately be reflected in the data structure.&nbsp; Now assume that the user wishes to cancel the data changes.&nbsp; Unfortunately the data structure has already been updated with the changes.&nbsp; How do you reset the data structure?
<br />
<br />There are probably 101 ways to solve this problem.&nbsp; One approach that works well and does not use data binding is to copy data from the data structure into the window elements for display and copy the data back from the window elements to the data structure for persistence.&nbsp; This is accomplished by writing two private methods, one to copy from the data structure to the window elements and the other to copy from the window elements to the data structure.&nbsp; The on change event from each editable window element can be wired to a single event handler that sets a flag that indicates data has changed, i.e., IsDirty.
<br />
<br />Within the form load event of the window, the private method to copy data from the structure to the window elements is called.&nbsp; Within the form close event or some other event indicating a desire to save the data, the private method to copy the data from the window elements to the data structure is called.&nbsp; The flag indicating data has changed can be used here to avoid copying data when no changes exist.&nbsp; In other words, only copy the data from the window elements if the IsDirty flag is true; otherwise do not copy the values.
<br />
<br />This approach does require the developer to write code.&nbsp; Data binding would of course eliminate the need to write the code but in doing so you give up some flexibility in what you can and cannot do.&nbsp; In many more complex solutions, giving up that flexibility can lead to more costly problem solving approaches such as writing code for workarounds to problems caused by the loss of flexibility.&nbsp; This can be true when data binding is used.&nbsp;
<br />
<br />I have seen projects that use data binding go down the path of writing various parsers, formatters, utility helper classes, implementing interfaces such as IEditableObject on data structures, and so on just to overcome limitations imposed by the use of data binding.&nbsp; In the attempt to avoid writing code that follows a straight forward pattern of moving data from a structure to window elements and back, the project developers have made life much harder for themselves.&nbsp; Design meetings, whiteboard sessions, and developer time are wasted on producing these workarounds just to eliminate the need to write simple snippets of clean code within the window.
<br />
<br />Data bind has its place in the application development world, but do not assume it is the only approach to use within your applications.&nbsp; Don't be afraid to write code.&nbsp; You might be surprised at how easy it is to maintain, enhance, and most importantly improve the richness of your applications when you don't use concepts like data binding.&nbsp; And when you do use data binding use it wisely.
<br />