---
title: Dodaj funkcję składową
ms.date: 11/09/2018
f1_keywords:
- vc.codewiz.classes.member.function
- vc.codewiz.function.overview
helpviewer_keywords:
- member functions, adding to classes
- classes [C++], adding members
- add member function wizard [C++]
ms.assetid: 55b25ddb-541d-44ed-957c-974ef91cfc85
ms.openlocfilehash: 1cd7abbbc43ae56861b3b83451b41933b8b0b4f0
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/24/2019
ms.locfileid: "64345996"
---
# <a name="add-a-member-function"></a>Dodaj funkcję składową

W **Widok klas**, można dodać funkcję członkowską do każdej klasy. Po wykonaniu tej deklaracji jest dodawana do pliku nagłówka i treści funkcji składowej klasy zastępczej jest dodawany do pliku implementacji klasy, którą można modyfikować.

**Aby dodać funkcję członkowską do klasy:**

1. W **Widok klas**, rozwiń węzeł projektu, aby wyświetlić klasy w projekcie. (Aby otworzyć **Widok klas**, na pasku menu wybierz **widoku**, **Widok klas**.)

1. Otwórz menu skrótów dla tej klasy, które chcesz dodać do funkcji składowej, a następnie wybierz **Dodaj**, **dodawania funkcji**.

1. Podaj odpowiednie szczegóły na temat funkcji elementu członkowskiego. Aby uzyskać więcej informacji, zobacz [Dodaj element członkowski funkcji kreatora](#add-member-function-wizard).

1. Wybierz **Zakończ** przycisk, aby wygenerować kod funkcji elementu członkowskiego.

## <a name="in-this-section"></a>W tej sekcji

- [Kreator dodawania funkcji członkowskiej](#add-member-function-wizard)

## <a name="add-member-function-wizard"></a>Kreator dodawania funkcji członkowskiej

Ten kreator dodaje deklarację funkcji członkowskiej do pliku nagłówka. Dodaje także implementacja funkcji składowej klasy zastępczej do pliku implementacji dla wybranej klasy.

Po dodaniu funkcji składowej za pomocą kreatora można edytować kod w środowisku programistycznym.

- **Zwracany typ**

  Ustawia typ zwracany dla funkcji członkowskiej dodawanego. Możesz podać swój własny typ zwracany, lub możesz wybrać z listy dostępnych typów. Aby uzyskać informacje o typach, zobacz [podstawowych typów](../cpp/fundamental-types-cpp.md).

  | | | |
  |---|---|---|
  | `char` | `int` | `unsigned int` |
  | `double` | `long` | `unsigned long` |
  | `float` | `short` | `void` |
  | `HRESULT` | `unsigned char` | |

- **Nazwa funkcji**

  Ustawia nazwę funkcji elementu członkowskiego, który dodajesz.

- **Typ parametru**

  Ustawia typ parametru dodawanego dla funkcji członkowskiej, jeśli funkcja elementu członkowskiego ma następujące parametry. Możesz podać swój własny typ parametru, lub możesz wybrać z listy dostępnych typów.

  | | | |
  |---|---|---|
  | `char` | `int` | `unsigned char` |
  | `double` | `long` | `unsigned int` |
  | `float` | `short` | `unsigned long` |

- **Nazwa parametru**

  Ustawia nazwę parametru dodawanego dla funkcji członkowskiej, jeśli funkcja elementu członkowskiego ma następujące parametry.

- **Lista parametrów**

  Wyświetla listę parametrów, które zostały dodane do funkcji składowej. Aby dodać parametr do listy, podać typ i nazwa w **typ parametru** i **Nazwa parametru** pola, a następnie wybierz pozycję **Dodaj**. Aby usunąć parametr z listy, wybierz parametr, a następnie wybierz pozycję **Usuń**.

- **Dostęp**

  Ustawia dostęp do funkcji składowej. Modyfikatory dostępu są słowami kluczowymi, określające dostęp, innych klas, że funkcja elementu członkowskiego. Aby uzyskać więcej informacji na temat określania dostępu, zobacz [kontroli dostępu do elementu członkowskiego](../cpp/member-access-control-cpp.md). Poziom dostępu do funkcji elementu członkowskiego jest równa `public` domyślnie.

  - [public](../cpp/public-cpp.md)
  - [protected](../cpp/protected-cpp.md)
  - [private](../cpp/private-cpp.md)

  Sprawdź, czy nowa funkcja elementu członkowskiego jest statyczny lub wirtualnych i czy jest to wbudowane lub czysty. Jeśli ustawisz czysty, funkcji elementu członkowskiego **wirtualnej** zaznaczono pole wyboru i **wbudowane** pole staje się niedostępny. Wartością domyślną jest funkcją składową Niestatyczne, niewirtualne.

  | Opcja | Opis |
  |--------|-------------|
  | [Static](../cpp/storage-classes-cpp.md) |  Określa, czy funkcja działa jak globalnym i może być wywołana poza klasy, nawet bez tworzenia wystąpienia klasy. Funkcja elementu członkowskiego nie ma dostępu do niestatycznych elementów członkowskich. Funkcja elementu członkowskiego, określony jako `Static` nie może być wirtualny. |
  | [Wirtualny](../cpp/virtual-cpp.md) | Sprawdza, czy funkcja poprawny element członkowski jest wywoływana dla obiektu, niezależnie od tego, wyrażenie używane do wywołania funkcji elementu członkowskiego. Funkcja elementu członkowskiego, określony jako `Virtual` nie może być statyczna. |
  | **czyste** | Wskazuje, że nie dostarczono żadnej implementacji dla deklarowanej funkcji wirtualnej składowej. **Czysty** można określić tylko dla funkcji wirtualnych elementów członkowskich. Klasa, która zawiera co najmniej jeden czystej wirtualnej funkcji składowej jest traktowany jako klasa abstrakcyjna. Klasy pochodne klasy abstrakcyjnej muszą implementować czystej wirtualnej funkcji składowej lub są one zbyt, klasy abstrakcyjne. |
  | [wbudowane](../cpp/inline-functions-cpp.md) | Instruuje kompilator, aby wstawić kopię treści funkcji składowej do każdego miejsca, którego funkcja członkowska jest wywoływana. Funkcja elementu członkowskiego, określony jako **wbudowane** nie może być czysty. |

- **Plik CPP**

  Ustawia lokalizację pliku, w którym zapisywana jest implementacja funkcji składowej klasy zastępczej. Domyślnie jest ona zapisywana w pliku .cpp dla klasy, do którego jest dodawana funkcja elementu członkowskiego. Wybierz przycisk wielokropka, aby zmienić nazwę pliku. Implementacja funkcji elementu członkowskiego jest dodawany do zawartość wybranego pliku.

- **Komentarz**

  Zawiera komentarz w pliku nagłówkowym dla funkcji członkowskiej.

- **Sygnatura funkcji**

  Wyświetla verbatim od kodu, funkcja elementu członkowskiego, po wybraniu **Zakończ**. Nie można edytować tekst w tym polu. Aby zmienić funkcja elementu członkowskiego, należy zmienić odpowiednie pola w kreatorze.
