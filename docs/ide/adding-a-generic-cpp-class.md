---
title: Dodawanie rodzajowej klasy C++
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
ms.openlocfilehash: 08ebe572da605e0f6d4d712bd7e48159598ba844
ms.sourcegitcommit: b032daf81cb5fdb1f5a988277ee30201441c4945
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/15/2018
ms.locfileid: "51694143"
---
# <a name="add-a-generic-c-class"></a>Dodawanie rodzajowej klasy C++

Można dodać rodzajowej klasy C++ za pomocą **Widok klas**. Rodzajowej klasy C++ jest klasą, który zdefiniujesz lub która pochodzi od klasy, który zdefiniujesz.

**Aby dodać rodzajowej klasy C++ do projektu:**

1. W **Widok klas**, kliknij prawym przyciskiem myszy projekt, do którego chcesz dodać nową klasę, wybierz **Dodaj**, a następnie wybierz **klasy**.

1. W [Dodaj klasę](../ide/add-class-dialog-box.md) w okienku szablonów, wybierz w oknie dialogowym **klasy języka C++**. Wybierz **Dodaj** do wyświetlenia [Kreatorze klasy generycznej C++](#generic-c-class-wizard).

1. W kreatorze podaj nazwę klasy, a następnie zdefiniuj ustawienia lub zaakceptuj wartości domyślne.

1. Aby zamknąć kreatora i Wyświetl nowe rodzajowej klasy C++ w projekcie, wybierz **Zakończ**.

## <a name="in-this-section"></a>W tej sekcji

- [Kreatorze klasy generycznej C++](#generic-c-class-wizard)

## <a name="generic-c-class-wizard"></a>Kreatorze klasy generycznej C++

Dodaje rodzajowej klasy C++ do projektu. Klasa nie dziedziczy ATL lub MFC.

- **Nazwa klasy**

  Określa nazwę nowej klasy.

- **plik .h**

  Określa nazwę pliku nagłówka dla nowej klasy. Domyślnie ta nazwa jest na podstawie nazwy podane **Nazwa klasy**. Aby zapisać plik nagłówkowy na lokalizację lub Dołącz deklaracji klasy do istniejącego pliku, kliknij przycisk wielokropka (**...** ). Jeśli określono istniejący plik i wybierz pozycję **Zakończ**, Kreator monituje o określenie, czy deklaracja klasy powinna zostać dołączona do zawartości pliku. Aby dołączyć deklaracji, wybierz **tak**; aby powrócić do kreatora i podaj inną nazwę pliku, wybierz **nie**.

- **Plik CPP**

  Określa nazwę pliku implementacji dla nowej klasy. Domyślnie ta nazwa jest na podstawie nazwy podane **Nazwa klasy**. Aby zapisać plik implementacji na lokalizację lub Dołącz definicję klasy do istniejącego pliku, kliknij przycisk wielokropka (**...** ). Jeśli określono istniejący plik i wybierz pozycję **Zakończ**, Kreator monituje o określenie, czy definicja klasy powinna zostać dołączona do zawartości pliku. Aby dołączyć definicji, wybierz **tak**; aby powrócić do kreatora i podaj inną nazwę pliku, wybierz **nie**.

- **Klasa bazowa**

  Ustawia klasę bazową dla nowej klasy.

- **Dostęp do**

  Ustawia dostęp do składowych klasy bazowej dla nowej klasy. Modyfikatory dostępu są słowami kluczowymi, które określają poziom dostępu, który inne klasy mają funkcji składowych klasy. Aby uzyskać więcej informacji o sposobie określania dostępu, zobacz [kontrola dostępu do składowych](../cpp/member-access-control-cpp.md). Domyślnie ustawiono poziom dostępu do klasy `public`.

  - `public`
  - `protected`
  - `private`
  - **Domyślne** (nie modyfikator dostępu jest generowany.)

- **Destruktor wirtualny**

  Określa, czy wirtualny destruktor klasy. Użyj wirtualnego destruktora pomaga, upewnij się, że poprawne destruktor jest wywoływany, usunięcie wystąpień klas pochodnych.

- **wbudowane**

  Generuje konstruktora klasy i definicji klasy, jak funkcje śródwierszowe w pliku nagłówkowym.

- **Zarządzane**

  Po wybraniu dodaje plik zarządzanych klas i nagłówek. Po wyczyszczeniu, dodaje macierzysty plik klasy i nagłówek.
