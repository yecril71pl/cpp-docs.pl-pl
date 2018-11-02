---
title: 'Porady: definiowanie i instalowanie globalnego programu obsługi wyjątków'
ms.date: 11/04/2016
helpviewer_keywords:
- handlers, global
ms.assetid: dd88a812-3bc7-4ce8-8283-4b674c246534
ms.openlocfilehash: 9c6f355bc43fc53d2b8d27a1ee69c059d0f50692
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50534540"
---
# <a name="how-to-define-and-install-a-global-exception-handler"></a>Porady: definiowanie i instalowanie globalnego programu obsługi wyjątków

Poniższy przykład kodu demonstruje sposób nieobsłużone wyjątki mogą być przechwytywane. Formularza zawiera przycisk, który, po naciśnięciu klawisza, wykonuje odwołanie o wartości null powoduje zgłoszenie wyjątku. Ta funkcja reprezentuje typowy kod błędu. Wynikowy wyjątek zostaje przechwycony przez program obsługi wyjątków całej aplikacji, instalowane przez funkcję main.

Jest to realizowane przez powiązanie delegat <xref:System.Windows.Forms.Application.ThreadException> zdarzeń. W tym przypadku kolejnych wyjątki są następnie wysyłane do `App::OnUnhandled` metody.

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