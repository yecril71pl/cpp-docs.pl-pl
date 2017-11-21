---
title: "Porady: odczytywanie liczników wydajności systemu Windows (C + +/ CLI) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- performance counters
- performance counters, reading Windows performance counters
- performance monitoring, Windows performance counters
- performance, counters
- counters, reading Windows performance counters
- performance
- performance monitoring
ms.assetid: 9e1c836c-cb0f-4f37-9a93-3dca6412d6b1
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 3ad77e459d32ed0fc0b3798d2a37b4754d556f20
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="how-to-read-windows-performance-counters-ccli"></a>Porady: odczytywanie liczników wydajności systemu Windows (C++/CLI)
Niektóre aplikacje i podsystemy Windows ujawniać dane wydajności za pośrednictwem wydajności systemu Windows. Te liczniki mogą uzyskać dostęp za pomocą <xref:System.Diagnostics.PerformanceCounterCategory> i <xref:System.Diagnostics.PerformanceCounter> klasy, które znajdują się w <xref:System.Diagnostics?displayProperty=fullName> przestrzeni nazw.  
  
 Poniższy przykład kodu wykorzystuje te klasy pobierania i wyświetlania licznika, która jest aktualizowana przez system Windows, aby wskazać procent czasu zajętości procesora.  
  
> [!NOTE]
>  W tym przykładzie wymaga uprawnień administracyjnych do uruchamiania w systemie Windows Vista.  
  
## <a name="example"></a>Przykład  
  
```  
// processor_timer.cpp  
// compile with: /clr  
#using <system.dll>  
  
using namespace System;  
using namespace System::Threading;  
using namespace System::Diagnostics;  
using namespace System::Timers;  
  
ref struct TimerObject  
{  
public:  
   static String^ m_instanceName;  
   static PerformanceCounter^ m_theCounter;  
  
public:  
   static void OnTimer(Object^ source, ElapsedEventArgs^ e)  
   {  
      try   
      {  
         Console::WriteLine("CPU time used: {0,6} ",  
          m_theCounter->NextValue( ).ToString("f"));  
      }   
      catch(Exception^ e)  
      {  
         if (dynamic_cast<InvalidOperationException^>(e))  
         {  
            Console::WriteLine("Instance '{0}' does not exist",  
                  m_instanceName);  
            return;  
         }  
         else  
         {  
            Console::WriteLine("Unknown exception... ('q' to quit)");  
            return;  
         }  
      }  
   }  
};  
  
int main()  
{  
   String^ objectName = "Processor";  
   String^ counterName = "% Processor Time";  
   String^ instanceName = "_Total";  
  
   try  
   {  
      if ( !PerformanceCounterCategory::Exists(objectName) )  
      {  
         Console::WriteLine("Object {0} does not exist", objectName);  
         return -1;  
      }  
   }  
   catch (UnauthorizedAccessException ^ex)  
   {  
      Console::WriteLine("You are not authorized to access this information.");  
      Console::Write("If you are using Windows Vista, run the application with ");  
      Console::WriteLine("administrative privileges.");  
      Console::WriteLine(ex->Message);  
      return -1;  
   }  
  
   if ( !PerformanceCounterCategory::CounterExists(  
          counterName, objectName) )  
   {  
      Console::WriteLine("Counter {0} does not exist", counterName);  
      return -1;  
   }  
  
   TimerObject::m_instanceName = instanceName;  
   TimerObject::m_theCounter = gcnew PerformanceCounter(  
          objectName, counterName, instanceName);  
  
   System::Timers::Timer^ aTimer = gcnew System::Timers::Timer();  
   aTimer->Elapsed += gcnew ElapsedEventHandler(&TimerObject::OnTimer);  
   aTimer->Interval = 1000;  
   aTimer->Enabled = true;  
   aTimer->AutoReset = true;  
  
   Console::WriteLine("reporting CPU usage for the next 10 seconds");  
   Thread::Sleep(10000);  
   return 0;  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie do monitorowania wydajności](http://msdn.microsoft.com/en-us/d40f10b9-e2b7-4ec8-a9b3-706929e5bf35)   
 [Operacje w systemie Windows (C + +/ CLI)](../dotnet/windows-operations-cpp-cli.md)   
 [.NET programowania w języku C + +/ CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)