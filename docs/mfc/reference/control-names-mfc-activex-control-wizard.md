---
title: Nazwy formantów, Kreator formantów MFC ActiveX | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.appwiz.mfc.ctl.names
dev_langs:
- C++
helpviewer_keywords:
- MFC ActiveX Control Wizard, control names
ms.assetid: 9b8b81d2-36df-48ed-b58a-a771a0e269ee
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 08a406bf633715f6a6e9546295da3b02a41f0063
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33369313"
---
# <a name="control-names-mfc-activex-control-wizard"></a>Nazwy kontrolek, kreator kontrolek ActiveX MFC
Określenie nazw klasy formantu i klasy strony właściwości, nazwy typów, a następnie wpisz identyfikatory dla formantu. Z wyjątkiem produktów **krótką nazwę**, wszystkich innych pól, które mogą być edytowane niezależnie. Jeśli zmienisz tekst **krótką nazwę**, znajduje odzwierciedlenie w nazwach wszystkich innych pól na tej stronie. To zachowanie nazewnictwa zaprojektowano w celu ułatwić wszystkich nazw identyfikację automatycznie podczas opracowywania formantu.  
  
 **Krótka nazwa**  
 Podaj skróconą nazwę formantu. Domyślnie ta nazwa jest na podstawie projektu nazwy podane w **nowy projekt** okno dialogowe. O podanej nazwie określa nazwy klasy, nazwy typu i identyfikatory typów, jeśli nie zmienisz tych pól pojedynczo.  
  
 **Nazwa klasy formantu**  
 Domyślnie nazwa klasy formantu opiera się na krótką nazwę z `C` jako prefiksu i `Ctrl` sufiks. Na przykład, jeśli formant krótka nazwa jest `Price`, jest nazwą klasy formantu `CPriceCtrl`.  
  
 **Plik .h sterowania**  
 Domyślnie, nazwa pliku nagłówka opiera się na krótką nazwę z `Ctrl` sufiks i `.h` jako rozszerzenie pliku. Na przykład, jeśli formant krótka nazwa jest `Price`, nazwa pliku nagłówka jest `PriceCtrl.h`. Nazwa tego pola powinna być zgodna z nazwą klasy formantu.  
  
 **Plik .cpp sterowania**  
 Domyślnie, nazwa pliku nagłówka opiera się na krótką nazwę z `Ctrl` sufiks i `.cpp` jako rozszerzenie pliku. Na przykład, jeśli formant krótka nazwa jest `Price`, nazwa pliku nagłówka jest `PriceCtrl.cpp`. Nazwa tego pola powinna odpowiadać nazwie nagłówka.  
  
 **Nazwa typu formantu**  
 Domyślnie, nazwa typu formantu opiera się na krótką nazwę, a następnie `Control`. Na przykład, jeśli formant krótka nazwa jest `Price`, nazwa typu klasy formantu jest `Price Control`. Zmiana wartości w tym polu, upewnij się, że nazwa wskazuje dziedziczenia.  
  
 **Identyfikator typu formantu**  
 Ustawia identyfikator formantu typu klasy formantu. Formant zapisuje ten ciąg w rejestrze, gdy jest ona dodawana do projektu. Aplikacje kontenera użyć tego ciągu do utworzenia wystąpienia formantu.  
  
 Domyślnie, identyfikator typu formantu opiera się na nazwę projektu, który wskazano w **nowy projekt** okno dialogowe i krótką nazwę. Ta nazwa powinna być zgodna z nazwą typu.  
  
 Domyślnie identyfikator typu formantu wygląda następująco:  
  
 *ProjectName.ShortName*Ctrl.1  
  
 Jeśli zmienisz krótkiej nazwy w tym oknie dialogowym, identyfikator typu formantu wygląda następująco:  
  
 *ProjectName.NewShortName*Ctrl.1  
  
 **Nazwa klasy PropPage**  
 Domyślnie nazwa klasy strony właściwości opiera się na krótką nazwę z `C` jako prefiksu i `PropPage` sufiks. Na przykład, jeśli formant krótka nazwa jest `Price`, nazwa klasy strony właściwości jest `CPricePropPage`. Ta nazwa powinna być zgodna z nazwą klasy formantu, dołączony `PropPage`.  
  
 **W pliku .h PropPage**  
 Domyślnie, nazwa pliku nagłówka strony właściwości jest oparta na krótką nazwę z jako `PropPage` sufiks i `.h` jako rozszerzenie pliku. Na przykład, jeśli formant krótka nazwa jest `Price`, nazwa pliku nagłówka strony właściwości jest `PricePropPage.h`. Ta nazwa powinna być zgodna z nazwą klasy.  
  
 **Plik .cpp PropPage**  
 Domyślnie, nazwa pliku implementacji strony właściwości jest oparta na krótką nazwę z jako `PropPage` sufiks i `.cpp` jako rozszerzenie pliku. Na przykład, jeśli formant krótka nazwa jest `Price`, nazwa pliku nagłówka strony właściwości jest `PricePropPage.cpp`. Ta nazwa powinna odpowiadać nazwie pliku nagłówka.  
  
 **Nazwa typu PropPage**  
 Domyślnie, nazwa typu strony właściwości jest oparta na krótką nazwę, a następnie `Property Page`. Na przykład, jeśli formant krótka nazwa jest `Price`, nazwa typu strony właściwości jest `Price Property Page`. Zmiana wartości w tym polu, upewnij się, że nazwa wskazuje klasy formantu.  
  
 **Identyfikator typu PropPage**  
 Ustawia identyfikator klasy strony właściwości. Formant zapisuje ten ciąg w rejestrze, po zastosowaniu do projektu. Aplikacji kontenera używa tego ciągu do utworzenia wystąpienia strony właściwości formantu.  
  
 Domyślnie, identyfikator typu strony właściwości opiera się na nazwę projektu, który wskazano w **nowy projekt** okno dialogowe i krótką nazwę. Ta nazwa powinna być zgodna z nazwą typu.  
  
 Domyślnie identyfikator typu strony właściwości wygląda następująco:  
  
 *ProjectName.ShortName*PropPage.1  
  
 Jeśli zmienisz krótkiej nazwy w tym oknie dialogowym, identyfikator typu strony właściwości wygląda następująco:  
  
 *ProjectName.NewShortName*PropPage.1  
  
## <a name="see-also"></a>Zobacz też  
 [Kreator kontrolek ActiveX MFC](../../mfc/reference/mfc-activex-control-wizard.md)   
 [Ustawienia aplikacji, Kreator kontrolek ActiveX MFC](../../mfc/reference/application-settings-mfc-activex-control-wizard.md)   
 [Sterowanie ustawieniami, Kreator kontrolek ActiveX MFC](../../mfc/reference/control-settings-mfc-activex-control-wizard.md)   
 [Typy plików utworzonych dla projektów Visual C++](../../ide/file-types-created-for-visual-cpp-projects.md)

