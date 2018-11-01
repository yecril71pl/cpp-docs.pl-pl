---
title: Dodawanie właściwości (Visual C++)
ms.date: 11/04/2016
helpviewer_keywords:
- interfaces, adding properties
- properties [C++], adding to interfaces
ms.assetid: 37bd4db7-efd3-4faa-87ad-64902ed16a36
ms.openlocfilehash: 3c47a5b50442f47e6042ea1232590dbdde7299ec
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50563088"
---
# <a name="adding-a-property-visual-c"></a>Dodawanie właściwości (Visual C++)

Możesz użyć [Kreator dodawania właściwości](../ide/names-add-property-wizard.md) Aby dodać metodę do interfejsu w projekcie.

### <a name="to-add-a-property-to-your-object"></a>Aby dodać właściwość do obiektu

1. W [Widok klas](/visualstudio/ide/viewing-the-structure-of-code), kliknij prawym przyciskiem myszy nazwę interfejsu, do którego chcesz dodać właściwość.

   > [!NOTE]
   > Można również dodać właściwości do dispinterfaces, który, chyba że projekt jest przypisane, są zagnieżdżone w obrębie węzła biblioteki.

1. W menu skrótów kliknij **Dodaj**, a następnie kliknij przycisk **Dodaj właściwość**.

1. W [Kreator dodawania właściwości](../ide/names-add-property-wizard.md), podaj informacje, aby utworzyć właściwość.

1. Określ jakiekolwiek ustawienia interfejsu definicja języka (IDL) dla właściwości w [atrybuty IDL](../ide/idl-attributes-add-property-wizard.md) strony kreatora.

1. Kliknij przycisk **Zakończ** można dodać właściwości.

**Uzyskać** i `Put` metody, właściwości są wyświetlane jako dwie ikony w widoku klas w obszarze interfejs, w którym jest zdefiniowana. Możesz kliknąć dwukrotnie albo ikonę, aby wyświetlić deklaracja właściwości w pliku .idl.

- Interfejsy ATL **uzyskać** i **umieścić** funkcje są dodawane do pliku .cpp i odwołania do tych funkcji są dodawane do pliku .h.

- Dla dispinterfaces MFC, jeśli zostanie wybrana **zmiennej składowej** jako typ implementacji metody i zmienna są dodawane do klasy, która implementuje go. Jeśli wybierzesz **metod Get/Set** jako typ implementacji dwie metody są dodawane do klasy, która implementuje go.

## <a name="see-also"></a>Zobacz też

[Tworzenie interfejsu COM](../ide/creating-a-com-interface-visual-cpp.md)<br>
[Edytowanie interfejsu COM](../ide/editing-a-com-interface.md)<br>
[Model Component Object Model](/windows/desktop/com/the-component-object-model)<br>
[Wskaźniki interfejsu i interfejsy](/windows/desktop/com/interface-pointers-and-interfaces)