---
title: Atrybuty IDL, Kreator dodawania metody
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.method.idlattrib
helpviewer_keywords:
- Add Method Wizard [C++]
- IDL attributes, Add Method Wizard
ms.assetid: f80c3bc1-b515-4d6c-83ee-98c2c21ba902
ms.openlocfilehash: 073f821d7db0733c89c21ed4b2a85014aa151244
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50615790"
---
# <a name="idl-attributes-add-method-wizard"></a>Atrybuty IDL, Kreator dodawania metody

Ta strona kreatora dodawania metody umożliwia Określ jakiekolwiek ustawienia interfejsu definicja języka (IDL) dla metody.

- **id**

   Ustawia identyfikator numeryczny, który identyfikuje metodę. Zobacz [identyfikator](/windows/desktop/Midl/id) w *odwołania MIDL*.

   To pole jest niedostępna dla interfejsów niestandardowych i nie jest dostępna dla MFC dispinterfaces.

- **call_as**

   Określa nazwę metody zdalnej, do którego ta metoda lokalne mogą być mapowane. Zobacz [call_as](/windows/desktop/Midl/call-as) w *odwołania MIDL*.

   Niedostępne dla MFC dispinterfaces.

- **helpcontext**

   Określa identyfikator kontekstu, który pozwala użytkownikowi oglądać informacje o tej metody w pliku pomocy. Zobacz [helpcontext —](/windows/desktop/Midl/helpcontext) w *odwołania MIDL*.

   Niedostępne dla MFC dispinterfaces.

- **helpstring**

   Określa ciąg znaków, który jest używany do opisania elementu, do której jest stosowany. Domyślnie jest ustawiona "Metoda *nazwę metody*." Zobacz [HelpString —](/windows/desktop/Midl/helpstring) w *odwołania MIDL*.

   Niedostępne dla MFC dispinterfaces.

- **Dodatkowe atrybuty**

   Niedostępne dla MFC dispinterfaces.

   |Atrybut|Opis|
   |---------------|-----------------|
   |**hidden**|Wskazuje, że metoda istnieje, ale nie powinien być wyświetlany w przeglądarce zorientowanej na użytkownika. Zobacz [ukryte](/windows/desktop/Midl/hidden) w *odwołania MIDL*.|
   |**source**|Wskazuje, że członek metoda jest źródłem zdarzeń. Zobacz [źródła](/windows/desktop/Midl/source) w *odwołania MIDL*.|
   |`local`|Określa kompilatorowi MIDL, metoda nie jest zdalny. Zobacz [lokalnego](/windows/desktop/Midl/local) w *odwołania MIDL*.|
   |**restricted**|Określa, że metoda nie może być wywoływana arbitralnie. Zobacz [ograniczeniami](/windows/desktop/Midl/restricted) w *odwołania MIDL*.|
   |**vararg**|Określa, że ta metoda przyjmuje zmienną liczbę argumentów. Aby to osiągnąć, ostatni argument musi być bezpieczną tablicą o **VARIANT** typ, który zawiera wszystkie pozostałe argumenty. Zobacz [vararg](/windows/desktop/Midl/vararg) w *odwołania MIDL*.|

## <a name="see-also"></a>Zobacz też

[Dodawanie metody](../ide/adding-a-method-visual-cpp.md)<br>
[Kreator dodawania metody](../ide/add-method-wizard.md)