---
title: Implementacja architektury wtyczki (C + +/ CLI) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- plug-ins [C++]
- reflection [C++}, plug-ins
ms.assetid: 4f31e42b-78d1-48b9-8fdc-f28c75e8e77e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 4e001ef88af0727a994c309d45167787d3e6677b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-implement-a-plug-in-component-architecture-using-reflection-ccli"></a>Porady: implementacja architektury składnika plug-in przy użyciu odbicia (C++/CLI)
W poniższych przykładach kodu przedstawiają sposób używania odbicia do zaimplementowania proste architektury "wtyczki". Pierwsze notowanie jest aplikacją, a drugą jest wartość wtyczki. Aplikacja jest wiele formularz dokumentu, który wypełnia się przy użyciu klasy bazującej na formularzu znaleziono w bibliotece DLL dodatku plug-in podany jako argument wiersza polecenia.  
  
 Aplikacja próbuje załadować zestaw udostępnionego przy użyciu <xref:System.Reflection.Assembly.Load%2A?displayProperty=fullName> metody. Jeśli powodzenia typów w zestawie są wyliczane przy użyciu <xref:System.Reflection.Assembly.GetTypes%2A?displayProperty=fullName> metody. Każdy typ są następnie sprawdzane pod kątem zgodności przy użyciu <xref:System.Type.IsAssignableFrom%2A?displayProperty=fullName> metody. W tym przykładzie musi być pochodną klasy znaleziony w zestawie podana <xref:System.Windows.Forms.Form> klasy na kwalifikować się jako dodatek typu plug-in.  
  
 Zgodne klas są następnie utworzono wystąpienie <xref:System.Activator.CreateInstance%2A?displayProperty=fullName> metodę, która akceptuje <xref:System.Type> jako argument i zwraca wskaźnik do nowego wystąpienia. Następnie dołączony do formularza i wyświetlić każdego nowego wystąpienia.  
  
 Należy pamiętać, że <xref:System.Reflection.Assembly.Load%2A> metoda nie akceptuje nazw zestawów, które obejmują rozszerzenia pliku. Funkcja main w aplikacji przycina wszystkich rozszerzeń podanego, więc Poniższy przykładowy kod działa w obu przypadkach.  
  
## <a name="example"></a>Przykład  
 Poniższy kod definiuje aplikację, która akceptuje dodatków plug-in. Należy podać nazwę zestawu jako pierwszego argumentu. Ten zestaw musi zawierać co najmniej jeden publiczny <xref:System.Windows.Forms.Form> typu pochodnego.  
  
```  
// plugin_application.cpp  
// compile with: /clr /c  
#using <system.dll>  
#using <system.drawing.dll>  
#using <system.windows.forms.dll>  
  
using namespace System;  
using namespace System::Windows::Forms;  
using namespace System::Reflection;  
  
ref class PluggableForm : public Form  {  
public:  
   PluggableForm() {}  
   PluggableForm(Assembly^ plugAssembly) {  
      Text = "plug-in example";  
      Size = Drawing::Size(400, 400);  
      IsMdiContainer = true;  
  
      array<Type^>^ types = plugAssembly->GetTypes( );  
      Type^ formType = Form::typeid;  
  
      for (int i = 0 ; i < types->Length ; i++) {  
         if (formType->IsAssignableFrom(types[i])) {  
            // Create an instance given the type description.  
            Form^ f = dynamic_cast<Form^> (Activator::CreateInstance(types[i]));  
            if (f) {  
               f->Text = types[i]->ToString();  
               f->MdiParent = this;  
               f->Show();  
            }  
         }  
      }  
   }  
};  
  
int main() {  
   Assembly^ a = Assembly::LoadFrom("plugin_application.exe");  
   Application::Run(gcnew PluggableForm(a));  
}  
```  
  
## <a name="example"></a>Przykład  
 Poniższy kod definiuje trzy klasy pochodzące od <xref:System.Windows.Forms.Form>. Gdy nazwa wynikowa Nazwa zestawu jest przekazywana do pliku wykonywalnego na poprzedniej liście, każda z tych trzech klas będą wykrywane i uruchomiony, mimo że zostały wszystkie nieznane do obsługi aplikacji w czasie kompilacji.  
  
```  
// plugin_assembly.cpp  
// compile with: /clr /LD  
#using <system.dll>  
#using <system.drawing.dll>  
#using <system.windows.forms.dll>  
  
using namespace System;  
using namespace System::Windows::Forms;  
using namespace System::Reflection;  
using namespace System::Drawing;  
  
public ref class BlueForm : public Form {  
public:  
   BlueForm() {  
      BackColor = Color::Blue;  
   }  
};  
  
public ref class CircleForm : public Form {  
protected:  
   virtual void OnPaint(PaintEventArgs^ args) override {  
      args->Graphics->FillEllipse(Brushes::Green, ClientRectangle);  
   }  
};  
  
public ref class StarburstForm : public Form {  
public:  
   StarburstForm(){  
      BackColor = Color::Black;  
   }  
protected:  
   virtual void OnPaint(PaintEventArgs^ args) override {  
      Pen^ p = gcnew Pen(Color::Red, 2);  
      Random^ r = gcnew Random( );  
      Int32 w = ClientSize.Width;  
      Int32 h = ClientSize.Height;  
      for (int i=0; i<100; i++) {  
         float x1 = w / 2;  
         float y1 = h / 2;  
         float x2 = r->Next(w);  
         float y2 = r->Next(h);  
         args->Graphics->DrawLine(p, x1, y1, x2, y2);  
      }  
   }  
};  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Odbicie (C++/CLI)](../dotnet/reflection-cpp-cli.md)