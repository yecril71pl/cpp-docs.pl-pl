---
title: "Porady: definiowanie i instalowanie globalnego programu obsługi wyjątków | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: handlers, global
ms.assetid: dd88a812-3bc7-4ce8-8283-4b674c246534
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 970ecd355b42c83102c034c4639f152b1971dae6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="how-to-define-and-install-a-global-exception-handler"></a>Porady: definiowanie i instalowanie globalnego programu obsługi wyjątków
Poniższy przykład kodu pokazuje sposób nieobsługiwanych wyjątków, można przechwycić. Przykład formularz zawiera przycisk, który po naciśnięciu wykonuje odwołanie o wartości null, powodując wyjątek zostanie wygenerowany. Ta funkcja reprezentuje błąd typowy kod. Wynikowa wyjątek zostanie przechwycony przez program obsługi wyjątku całej aplikacji zainstalowanych przez funkcję głównego.  
  
 Jest to osiągane przez powiązanie pełnomocnika, aby <xref:System.Windows.Forms.Application.ThreadException> zdarzeń. W takim przypadku kolejnych wyjątki są następnie wysyłane do `App::OnUnhandled` metody.  
  
## <a name="example"></a>Przykład  
  
```  
// global_exception_handler.cpp  
// compile with: /clr  
#using <system.dll>  
#using <system.drawing.dll>  
#using <system.windows.forms.dll>  
  
using namespace System;  
using namespace System::Threading;  
using namespace System::Drawing;  
using namespace System::Windows::Forms;  
  
ref class MyForm : public Form  
{  
   Button^ b;  
public:  
   MyForm( )  
   {  
      b = gcnew Button( );  
      b->Text = "Do Null Access";  
      b->Size = Drawing::Size(150, 30);  
      b->Click += gcnew EventHandler(this, &MyForm::OnClick);  
      Controls->Add(b);  
   }  
   void OnClick(Object^ sender, EventArgs^ args)   
   {  
      // do something illegal, like call through a null pointer...  
      Object^ o = nullptr;  
      o->ToString( );        
   }  
};  
  
ref class App  
{  
public:  
   static void OnUnhandled(Object^ sender, ThreadExceptionEventArgs^ e)  
   {  
      MessageBox::Show(e->Exception->Message, "Global Exeception");  
      Application::ExitThread( );  
   }  
};  
  
int main()  
{  
   Application::ThreadException += gcnew   
      ThreadExceptionEventHandler(App::OnUnhandled);  
  
   MyForm^ form = gcnew MyForm( );  
   Application::Run(form);  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa wyjątków](../windows/exception-handling-cpp-component-extensions.md)