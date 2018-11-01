---
title: Kreator klasy generycznej C++
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.class.generic
helpviewer_keywords:
- Generic C++ Class Wizard [C++]
ms.assetid: aa95be9e-fc1b-45db-a11d-0d32c4929077
ms.openlocfilehash: e3db091585615dcdccaab7c99c18a923802b31a7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50451041"
---
# <a name="generic-c-class-wizard"></a>Kreator klasy generycznej C++

Dodaje rodzajowej klasy C++ do projektu. Klasa nie dziedziczy ATL lub MFC.

- **Nazwa klasy**

   Określa nazwę nowej klasy.

- **plik .h**

   Określa nazwę pliku nagłówka dla nowej klasy. Domyślnie ta nazwa jest na podstawie nazwy podane **Nazwa klasy**. Aby zapisać plik nagłówkowy na lokalizację lub Dołącz deklaracji klasy do istniejącego pliku, kliknij przycisk oznaczony wielokropkiem (**...** ). Jeśli określisz istniejącego pliku, po kliknięciu **Zakończ**, Kreator monituje o określenie, czy deklaracja klasy powinna zostać dołączona do zawartości pliku. Aby dołączyć deklaracji, kliknij przycisk **tak**; aby powrócić do kreatora i podaj inną nazwę pliku, kliknij przycisk **nie**.

- **Plik CPP**

   Określa nazwę pliku implementacji dla nowej klasy. Domyślnie ta nazwa jest na podstawie nazwy podane **Nazwa klasy**. Aby zapisać plik implementacji na lokalizację lub Dołącz definicję klasy do istniejącego pliku, kliknij przycisk oznaczony wielokropkiem (**...** ). Jeśli określisz istniejącego pliku, po kliknięciu **Zakończ**, Kreator monituje o określenie, czy definicja klasy powinna zostać dołączona do zawartości pliku. Aby dołączyć definicji, kliknij przycisk **tak**; aby powrócić do kreatora i podaj inną nazwę pliku, kliknij przycisk **nie**.

- **Klasa bazowa**

   Ustawia klasę bazową dla nowej klasy.

- **Dostęp do**

   Ustawia dostęp do składowych klasy bazowej dla nowej klasy. Modyfikatory dostępu są słowami kluczowymi, które określają poziom dostępu, który inne klasy mają funkcji składowych klasy. Aby uzyskać więcej informacji o sposobie określania dostępu, zobacz [kontrola dostępu do składowych](../cpp/member-access-control-cpp.md). Domyślnie ustawiono poziom dostępu do klasy `public`.

   - `public`

   - `protected`

   - `private`

   - **Domyślne** (nie modyfikator dostępu jest generowany.)

- **Destruktor wirtualny**

   Określa, czy wirtualny destruktor klasy. Użyj wirtualnego destruktora pomaga upewnić się, że poprawne destruktor jest wywoływany, usunięcie wystąpień klas pochodnych.

- **wbudowane**

   Generuje konstruktora klasy i definicji klasy, jak funkcje śródwierszowe w pliku nagłówkowym.

- **Zarządzane**

   Po wybraniu dodaje plik zarządzanych klas i nagłówek. Po wyczyszczeniu, dodaje macierzysty plik klasy i nagłówek.

## <a name="see-also"></a>Zobacz też

[Dodawanie rodzajowej klasy C++](../ide/adding-a-generic-cpp-class.md)