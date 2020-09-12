---
title: Dodawanie funkcji składowej
ms.date: 11/09/2018
f1_keywords:
- vc.codewiz.classes.member.function
- vc.codewiz.function.overview
helpviewer_keywords:
- member functions, adding to classes
- classes [C++], adding members
- add member function wizard [C++]
ms.assetid: 55b25ddb-541d-44ed-957c-974ef91cfc85
ms.openlocfilehash: 0e63771e3e01c3829e20d2fe62fa2caf0f8b26f5
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2020
ms.locfileid: "90040785"
---
# <a name="add-a-member-function"></a>Dodawanie funkcji składowej

W **Widok klasy**można dodać funkcję członkowską do dowolnej klasy. Gdy to zrobisz, deklaracja jest dodawana do pliku nagłówkowego, a do pliku implementacji klasy zostanie dodana treść funkcji składowej, którą można następnie zmodyfikować.

**Aby dodać funkcję członkowską do klasy:**

1. W **Widok klasy**rozwiń węzeł projektu, aby wyświetlić klasy w projekcie. (Aby otworzyć **Widok klasy**, na pasku menu wybierz **Widok**, **Widok klasy**.)

1. Otwórz menu skrótów dla klasy, do której chcesz dodać funkcję członkowską, a następnie wybierz **Dodaj**, **Dodaj funkcję**.

1. Podaj odpowiednie szczegóły dotyczące funkcji członkowskiej. Aby uzyskać więcej informacji, zobacz [Kreator dodawania funkcji członkowskiej](#add-member-function-wizard).

1. Wybierz przycisk **Zakończ** , aby wygenerować kod funkcji składowej.

## <a name="in-this-section"></a>W tej sekcji

- [Kreator dodawania funkcji członkowskiej](#add-member-function-wizard)

## <a name="add-member-function-wizard"></a>Kreator dodawania funkcji członkowskiej

Ten Kreator dodaje deklarację funkcji składowej do pliku nagłówkowego. Dodaje również do pliku implementacji, implementację funkcji składowej dla wybranej klasy.

Po dodaniu funkcji składowej za pomocą kreatora można edytować kod w środowisku deweloperskim.

- **Typ zwracany**

  Ustawia zwracany typ dla funkcji członkowskiej, która jest dodawana. Możesz podać własny typ zwracany lub wybrać z listy dostępnych typów. Aby uzyskać informacje o typach, zobacz [podstawowe typy](../cpp/fundamental-types-cpp.md).

:::row:::
   :::column span="":::
      **`char`**\
      **`double`**\
      **`float`**\
      **`int`**
   :::column-end:::
   :::column span="":::
      **`long`**\
      **`short`**\
      **`unsigned char`**\
      **`unsigned int`**
   :::column-end:::
   :::column span="":::
      **`unsigned long`**\
      **`void`**\
      `HRESULT`
   :::column-end:::
:::row-end:::

- **Nazwa funkcji**

  Ustawia nazwę funkcji członkowskiej, która jest dodawana.

- **Typ parametru**

  Ustawia typ parametru, który jest dodawany do funkcji członkowskiej, jeśli funkcja członkowska ma parametry. Możesz podać własny typ parametru lub można wybrać z listy dostępnych typów.

:::row:::
   :::column span="":::
      **`char`**\
      **`double`**\
      **`float`**
   :::column-end:::
   :::column span="":::
      **`int`**\
      **`long`**\
      **`short`**
   :::column-end:::
   :::column span="":::
      **`unsigned char`**\
      **`unsigned int`**\
      **`unsigned long`**
   :::column-end:::
:::row-end:::

- **Nazwa parametru**

  Ustawia nazwę parametru, który jest dodawany do funkcji członkowskiej, jeśli funkcja członkowska ma parametry.

- **Lista parametrów**

  Wyświetla listę parametrów dodanych do funkcji członkowskiej. Aby dodać parametr do listy, podaj typ i nazwę w polach **Typ parametru** i **Nazwa parametru** i wybierz pozycję **Dodaj**. Aby usunąć parametr z listy, wybierz parametr, a następnie wybierz pozycję **Usuń**.

- **Dostęp**

  Ustawia dostęp do funkcji członkowskiej. Modyfikatory dostępu są słowami kluczowymi, które określają dostęp innych klas do funkcji składowej. Aby uzyskać więcej informacji o określaniu dostępu, zobacz [Kontrola dostępu do elementów członkowskich](../cpp/member-access-control-cpp.md). Poziom dostępu do funkcji składowych jest domyślnie ustawiony na wartość **`public`** .

  - [public](../cpp/public-cpp.md)
  - [protected](../cpp/protected-cpp.md)
  - [private](../cpp/private-cpp.md)

  Sprawdź, czy nowa funkcja członkowska jest statyczna, wirtualna i czy jest wbudowana, czy czysta. Jeśli ustawisz czystą funkcję elementu członkowskiego, pole wyboru **wirtualne** jest zaznaczone, a **wbudowane** pole wyboru stanie się niedostępne. Wartość domyślna to niestatyczna, niewirtualna funkcja członkowska.

  | Opcja | Opis |
  |--------|-------------|
  | [Statyczny](../cpp/storage-classes-cpp.md) |  Określa, że funkcja działa jak Global i może być wywoływana poza klasą, nawet bez tworzenia wystąpienia klasy. Funkcja członkowska nie ma dostępu do niestatycznych elementów członkowskich. Funkcja członkowska określona jako `Static` nie może być wirtualna. |
  | [Wirtualnej](../cpp/virtual-cpp.md) | Upewnij się, że jest wywoływana poprawna funkcja członkowska dla obiektu, niezależnie od wyrażenia użytego do wywołania funkcji składowej. Funkcja członkowska określona jako `Virtual` nie może być statyczna. |
  | **Dotyczy** | Wskazuje, że nie podano implementacji dla zadeklarowanej wirtualnej funkcji członkowskiej. **Czysty** można określić tylko w przypadku wirtualnych funkcji Członkowskich. Klasa, która zawiera co najmniej jedną czystą wirtualną funkcję członkowską, jest uznawana za klasę abstrakcyjną. Klasy pochodne klasy abstrakcyjnej muszą implementować czystą wirtualną funkcję członkowską lub są one również klasami abstrakcyjnymi. |
  | [Alert](../cpp/inline-functions-cpp.md) | Instruuje kompilator, aby wstawiał kopię treści funkcji składowej w każdym miejscu, w którym wywoływana jest funkcja członkowska. Funkcja członkowska określona jako **wbudowana** nie może być czysta. |

- **plik. cpp**

  Ustawia lokalizację pliku, w którym zapisywana jest implementacja funkcji składowej. Domyślnie jest on zapisywana w pliku CPP dla klasy, do której zostanie dodana funkcja członkowska. Wybierz przycisk wielokropka, aby zmienić nazwę pliku. Implementacja funkcji składowej jest dodawana do zawartości wybranego pliku.

- **Komentarz**

  Zawiera komentarz w pliku nagłówkowym dla funkcji członkowskiej.

- **Sygnatura funkcji**

  Wyświetla funkcję elementu członkowskiego Verbatim z kodu po wybraniu **przycisku Zakończ**. Nie można edytować tekstu w tym polu. Aby zmienić funkcję członkowską, należy zmienić odpowiednie pola w kreatorze.
