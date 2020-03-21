---
title: Nazwy kontrolek, kreator kontrolek ActiveX MFC
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.mfc.ctl.names
helpviewer_keywords:
- MFC ActiveX Control Wizard, control names
ms.assetid: 9b8b81d2-36df-48ed-b58a-a771a0e269ee
ms.openlocfilehash: eff7b537e7fe5c19d10cce8766557a3d1ff49342
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2020
ms.locfileid: "80077503"
---
# <a name="control-names-mfc-activex-control-wizard"></a>Nazwy kontrolek, kreator kontrolek ActiveX MFC

Określ nazwy klasy kontrolki i klasy strony właściwości, nazwy typów i identyfikatory typów dla kontrolki. Z wyjątkiem **krótkiej nazwy**wszystkie inne pola można edytować niezależnie. Jeśli zmienisz tekst **skróconej nazwy**, zmiana zostanie odzwierciedlona w nazwach wszystkich innych pól na tej stronie. Takie zachowanie nazewnictwa zostało zaprojektowane, aby wszystkie nazwy były łatwo rozpoznawalne podczas tworzenia kontrolki.

- **Krótka nazwa**

   Podaj skróconą nazwę formantu. Domyślnie ta nazwa jest oparta na nazwie projektu podanej w oknie dialogowym **Nowy projekt** . Wprowadzona nazwa określa nazwy klas, nazwy typów i identyfikatory typów, chyba że te pola są zmieniane pojedynczo.

- **Nazwa klasy kontrolki**

   Domyślnie nazwa klasy kontrolki jest oparta na krótkiej nazwie, z `C` jako prefiks i `Ctrl` jako sufiks. Na przykład, jeśli krótka nazwa kontrolki jest `Price`, nazwa klasy kontrolki jest `CPriceCtrl`.

- **Plik Control. h**

   Domyślnie nazwa pliku nagłówka jest oparta na krótkiej nazwie, z `Ctrl` jako sufiks i `.h` jako rozszerzenie pliku. Na przykład, jeśli krótka nazwa kontrolki jest `Price`, nazwa pliku nagłówka jest `PriceCtrl.h`. Nazwa w tym polu powinna być zgodna z nazwą klasy formantu.

- **Plik CPP kontrolki**

   Domyślnie nazwa pliku nagłówka jest oparta na krótkiej nazwie, z `Ctrl` jako sufiks i `.cpp` jako rozszerzenie pliku. Na przykład, jeśli krótka nazwa kontrolki jest `Price`, nazwa pliku nagłówka jest `PriceCtrl.cpp`. Nazwa w tym polu powinna być zgodna z nazwą nagłówka.

- **Nazwa typu formantu**

   Domyślnie nazwa typu formantu jest oparta na krótkiej nazwie, a następnie `Control`. Na przykład, jeśli krótka nazwa kontrolki jest `Price`, nazwa typu klasy kontrolki jest `Price Control`. Jeśli zmienisz wartość w tym polu, upewnij się, że nazwa wskazuje dziedziczenie.

- **Identyfikator typu formantu**

   Ustawia identyfikator typu kontrolki klasy formantu. Formant zapisuje ten ciąg w rejestrze, gdy zostanie on dodany do projektu. Aplikacje kontenera używają tego ciągu do tworzenia wystąpienia formantu.

   Domyślnie identyfikator typu formantu jest określany na podstawie nazwy projektu, który został wskazany w oknie dialogowym **Nowy projekt** i krótka nazwa. Ta nazwa powinna być zgodna z nazwą typu.

   Domyślnie identyfikator typu formantu jest wyświetlany w następujący sposób:

   *ProjectName. ShortName* Ctrl. 1

   Jeśli zmienisz krótką nazwę w tym oknie dialogowym, identyfikator typu formantu zostanie wyświetlony w następujący sposób:

   *ProjectName. NewShortName* Ctrl. 1

- **Nazwa klasy PropPage**

   Domyślnie nazwa klasy strony właściwości jest oparta na krótkiej nazwie, z `C` jako prefiks i `PropPage` jako sufiks. Na przykład, jeśli krótka nazwa kontrolki jest `Price`, nazwa klasy strony właściwości jest `CPricePropPage`. Ta nazwa powinna być zgodna z nazwą klasy formantu, dołączoną do `PropPage`.

- **Plik PropPage. h**

   Domyślnie nazwa pliku nagłówka strony właściwości jest oparta na krótkiej nazwie, za pomocą jako `PropPage` jako sufiksu i `.h` jako rozszerzenie pliku. Na przykład, jeśli krótka nazwa kontrolki jest `Price`, nazwa pliku nagłówka strony właściwości jest `PricePropPage.h`. Ta nazwa powinna być zgodna z nazwą klasy.

- **Plik PropPage. cpp**

   Domyślnie nazwa pliku implementacji strony właściwości jest oparta na krótkiej nazwie, za pomocą jako `PropPage` jako sufiksu i `.cpp` jako rozszerzenie pliku. Na przykład, jeśli krótka nazwa kontrolki jest `Price`, nazwa pliku nagłówka strony właściwości jest `PricePropPage.cpp`. Ta nazwa powinna być zgodna z nazwą pliku nagłówkowego.

- **Nazwa typu PropPage**

   Domyślnie nazwa typu strony właściwości jest oparta na krótkiej nazwie, a następnie `Property Page`. Na przykład, jeśli krótka nazwa kontrolki jest `Price`, nazwa typu strony właściwości jest `Price Property Page`. Jeśli zmienisz wartość w tym polu, upewnij się, że nazwa wskazuje klasę kontrolki.

- **Identyfikator typu PropPage**

   Ustawia identyfikator klasy strony właściwości. Formant zapisuje ten ciąg w rejestrze, gdy zostanie on zastosowany do projektu. Aplikacja kontenera używa tego ciągu do utworzenia wystąpienia strony właściwości kontrolki.

   Domyślnie identyfikator typu strony właściwości jest oparty na nazwie projektu, który został wskazany w oknie dialogowym **Nowy projekt** i krótka nazwa. Ta nazwa powinna być zgodna z nazwą typu.

   Domyślnie identyfikator typu strony właściwości jest wyświetlany w następujący sposób:

   *ProjectName. ShortName* PropPage. 1

   Jeśli zmienisz krótką nazwę w tym oknie dialogowym, identyfikator typu strony właściwości będzie wyświetlany w następujący sposób:

   *ProjectName. NewShortName* PropPage. 1

## <a name="see-also"></a>Zobacz też

[Kreator kontrolek ActiveX MFC](../../mfc/reference/mfc-activex-control-wizard.md)<br/>
[Ustawienia aplikacji, kreator kontrolek ActiveX MFC](../../mfc/reference/application-settings-mfc-activex-control-wizard.md)<br/>
[Ustawienia kontrolki, kreator kontrolek ActiveX MFC](../../mfc/reference/control-settings-mfc-activex-control-wizard.md)<br/>
[Typy plików utworzone dla projektów programu C++ Visual Studio](../../build/reference/file-types-created-for-visual-cpp-projects.md)
