---
title: Dodawanie klasy ogólnej C++
ms.date: 11/09/2018
f1_keywords:
- vc.codewiz.classes.adding.generic
- vc.codewiz.class.generic
helpviewer_keywords:
- Visual C++, classes
- generic classes, adding
- generic classes
- generic C++ class wizard [C++]
ms.assetid: e95a5a14-dbed-4edc-8551-344fe48613cb
ms.openlocfilehash: e81ea442578e69bdd28301eba8f70561f6aa76c6
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230548"
---
# <a name="add-a-generic-c-class"></a>Dodawanie klasy ogólnej C++

Można dodać generyczną klasę C++ za pomocą **Widok klasy**. Ogólna Klasa C++ jest klasą, która jest definiowana lub pochodną klasy zdefiniowanej przez użytkownika.

**Aby dodać ogólną klasę C++ do projektu:**

1. W **Widok klasy**kliknij prawym przyciskiem myszy projekt, do którego chcesz dodać nową klasę, wybierz polecenie **Dodaj**, a następnie wybierz pozycję **Klasa**.

1. W oknie dialogowym [Dodawanie klasy](../ide/add-class-dialog-box.md) w okienku szablony wybierz pozycję **Klasa C++**. Wybierz pozycję **Dodaj** , aby wyświetlić [Kreatora ogólnej klasy języka C++](#generic-c-class-wizard).

1. W Kreatorze Podaj nazwę klasy, a następnie Zdefiniuj ustawienia lub zaakceptuj ustawienia domyślne.

1. Aby zamknąć kreatora i wyświetlić nową klasę generyczną języka C++ w projekcie, wybierz pozycję **Zakończ**.

## <a name="in-this-section"></a>W tej sekcji

- [Kreator klasy generycznej C++](#generic-c-class-wizard)

## <a name="generic-c-class-wizard"></a>Kreator klasy generycznej C++

Dodaje rodzajową klasę C++ do projektu. Klasa nie dziedziczy z ATL ani MFC.

- **Nazwa klasy**

  Ustawia nazwę nowej klasy.

- **plik h**

  Ustawia nazwę pliku nagłówka dla nowej klasy. Domyślnie ta nazwa jest oparta na nazwie podanym w polu **Nazwa klasy**. Aby zapisać plik nagłówkowy w wybranej lokalizacji lub dołączyć deklarację klasy do istniejącego pliku, wybierz przycisk wielokropka (**...**). Jeśli określisz istniejący plik i wybierzesz przycisk **Zakończ**, Kreator monituje o określenie, czy deklaracji klasy należy dołączyć do zawartości pliku. Aby dołączyć deklarację, wybierz pozycję **tak**. Aby powrócić do kreatora i określić inną nazwę pliku, wybierz pozycję **nie**.

- **plik. cpp**

  Ustawia nazwę pliku implementacji dla nowej klasy. Domyślnie ta nazwa jest oparta na nazwie podanym w polu **Nazwa klasy**. Aby zapisać plik implementacji do wybranej lokalizacji lub dołączyć definicję klasy do istniejącego pliku, wybierz przycisk wielokropka (**...**). Jeśli określisz istniejący plik i wybierzesz przycisk **Zakończ**, Kreator monituje o określenie, czy definicja klasy powinna być dołączana do zawartości pliku. Aby dołączyć definicję, wybierz pozycję **tak**. Aby powrócić do kreatora i określić inną nazwę pliku, wybierz pozycję **nie**.

- **Klasa bazowa**

  Ustawia klasę bazową dla nowej klasy.

- **Dostęp**

  Ustawia dostęp do elementów członkowskich klasy bazowej dla nowej klasy. Modyfikatory dostępu są słowami kluczowymi, które określają poziom dostępu innych klas do funkcji składowych klasy. Aby uzyskać więcej informacji na temat sposobu określania dostępu, zobacz [Członkowie kontroli dostępu](../cpp/member-access-control-cpp.md). Domyślnie poziom dostępu do klasy jest ustawiony na **`public`** .

  - **`public`**
  - **`protected`**
  - **`private`**
  - **Wartość domyślna** (nie jest generowany modyfikator dostępu).

- **Destruktor wirtualny**

  Określa, czy destruktor klasy jest wirtualny. Użycie destruktora wirtualnego pomaga upewnić się, że w przypadku usunięcia wystąpień klas pochodnych zostanie wywołany poprawny destruktor.

- **Alert**

  Generuje zarówno konstruktora klasy, jak i definicję klasy jako funkcje wbudowane w pliku nagłówkowym.

- **Zarządzany**

  Po wybraniu program dodaje zarządzaną klasę i plik nagłówkowy. Po wyczyszczeniu, dodaje klasę natywną i plik nagłówkowy.
