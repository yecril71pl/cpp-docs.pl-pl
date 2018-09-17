---
title: Nazwy kontrolek, Kreator kontrolek ActiveX MFC | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 6d8342c76e58b5d21f36147f073e1380fbad15bd
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45712117"
---
# <a name="control-names-mfc-activex-control-wizard"></a>Nazwy kontrolek, kreator kontrolek ActiveX MFC
Określ nazwy klasy kontrolki i klasy strony właściwości, nazwy typów, a następnie wpisz identyfikatory dla kontrolki. Z wyjątkiem produktów **krótką nazwę**, wszystkie inne pola, które mogą być edytowane niezależnie. Jeśli zmienisz tekst **krótką nazwę**, zmiany są widoczne w nazwach wszystkich innych pól na tej stronie. To zachowanie nazewnictwa zaprojektowaną do podejmowania wszystkich nazw można łatwo zidentyfikować dla Ciebie podczas tworzenia kontrolki.  
  
- **Krótka nazwa**

   Podaj skróconą nazwę dla formantu. Domyślnie ta nazwa opiera się na nazwę projektu, podany w **nowy projekt** okno dialogowe. Podana nazwa określa nazwy klas, nazwy typów i identyfikatory typów, chyba że zmienił się tych pól indywidualnie.  
  
- **Nazwa klasy kontrolki**

   Domyślnie, nazwa klasy kontrolki opiera się na krótką nazwę z `C` jako prefiksu i `Ctrl` jako sufiks. Na przykład, jeśli formant użytkownika krótka nazwa jest `Price`, nazwa klasy kontrolki jest `CPriceCtrl`.  
  
- **Plik h kontrolki**

   Domyślnie, nazwa pliku nagłówkowego opiera się na krótką nazwę z `Ctrl` jako sufiks i `.h` jako rozszerzenie pliku. Na przykład, jeśli formant użytkownika krótka nazwa jest `Price`, nazwa pliku nagłówka to `PriceCtrl.h`. Nazwa tego pola powinna być zgodna Nazwa klasy kontrolki.  
  
- **Plik CPP kontrolki**

   Domyślnie, nazwa pliku nagłówkowego opiera się na krótką nazwę z `Ctrl` jako sufiks i `.cpp` jako rozszerzenie pliku. Na przykład, jeśli formant użytkownika krótka nazwa jest `Price`, nazwa pliku nagłówka to `PriceCtrl.cpp`. Nazwa tego pola powinna odpowiadać nazwie nagłówka.  
  
- **Nazwa typu kontrolki**

   Domyślnie, nazwa typu kontrolki opiera się na krótką nazwę, a następnie `Control`. Na przykład, jeśli formant użytkownika krótka nazwa jest `Price`, nazwa typu klasy kontrolki jest `Price Control`. Jeśli zmienisz wartość w tym polu, upewnij się, że nazwa wskazuje dziedziczenia.  
  
- **Identyfikator typu kontrolki**

   Ustawia identyfikator typu kontrolki klasy kontrolki. Kontrolka zapisuje ten ciąg w rejestrze, gdy zostanie dodany do projektu. Aplikacje kontenera Użyj tych parametrów do utworzenia wystąpienia formantu.  
  
   Domyślnie, identyfikator typu kontrolki opiera się na nazwę projektu, a wskazany w **nowy projekt** okno dialogowe i krótkiej nazwy. Ta nazwa powinna odpowiadać nazwie typu.  
  
   Domyślnie identyfikator typu kontrolki wygląda następująco:  
  
   *ProjectName.ShortName*Ctrl.1  
  
   Jeśli zmienisz krótką nazwę w oknie dialogowym, identyfikator typu kontrolki wygląda następująco:  
  
   *ProjectName.NewShortName*Ctrl.1  
  
- **Nazwa klasy PropPage**

   Domyślnie, nazwa klasy strony właściwości opiera się na krótką nazwę z `C` jako prefiksu i `PropPage` jako sufiks. Na przykład, jeśli formant użytkownika krótka nazwa jest `Price`, nazwa klasy strony właściwości jest `CPricePropPage`. Ta nazwa powinna odpowiadać Nazwa klasy kontrolki z dołączonym `PropPage`.  
  
- **Plik h PropPage**

   Domyślnie, nazwa pliku nagłówka strony właściwości opiera się na krótką nazwę z jako `PropPage` jako sufiks i `.h` jako rozszerzenie pliku. Na przykład, jeśli formant użytkownika krótka nazwa jest `Price`, nazwa pliku nagłówka strony właściwości jest `PricePropPage.h`. Ta nazwa powinna odpowiadać nazwie klasy.  
  
- **Plik CPP PropPage**

   Domyślnie, nazwa pliku implementacji strony właściwości opiera się na krótką nazwę z jako `PropPage` jako sufiks i `.cpp` jako rozszerzenie pliku. Na przykład, jeśli formant użytkownika krótka nazwa jest `Price`, nazwa pliku nagłówka strony właściwości jest `PricePropPage.cpp`. Ta nazwa powinna odpowiadać nazwie pliku nagłówka.  
  
- **Nazwa typu PropPage**

   Domyślnie, nazwa typu strony właściwości opiera się na krótką nazwę, a następnie `Property Page`. Na przykład, jeśli formant użytkownika krótka nazwa jest `Price`, nazwa typu strony właściwości jest `Price Property Page`. Jeśli zmienisz wartość w tym polu, upewnij się, że wskazuje nazwa klasy kontrolki.  
  
- **Identyfikator typu PropPage**

   Ustawia identyfikator klasy strony właściwości. Kontrolka zapisuje ten ciąg w rejestrze, stosowania do projektu. Aplikacja kontenera używa tego ciągu do utworzenia wystąpienia strona właściwości formantu.  
  
   Domyślnie, identyfikator typu strony właściwości opiera się na nazwę projektu, a wskazany w **nowy projekt** okno dialogowe i krótkiej nazwy. Ta nazwa powinna odpowiadać nazwie typu.  
  
   Domyślnie identyfikator typu strony właściwości wygląda następująco:  
  
   *ProjectName.ShortName*PropPage.1  
  
   Jeśli zmienisz krótką nazwę w oknie dialogowym, identyfikator typu strony właściwości wygląda następująco:  
  
   *ProjectName.NewShortName*PropPage.1  
  
## <a name="see-also"></a>Zobacz też  
 [Kreator kontrolek ActiveX MFC](../../mfc/reference/mfc-activex-control-wizard.md)   
 [Ustawienia aplikacji, Kreator kontrolek ActiveX MFC](../../mfc/reference/application-settings-mfc-activex-control-wizard.md)   
 [Ustawienia kontrolki, Kreator kontrolek ActiveX MFC](../../mfc/reference/control-settings-mfc-activex-control-wizard.md)   
 [Typy plików utworzonych dla projektów Visual C++](../../ide/file-types-created-for-visual-cpp-projects.md)

