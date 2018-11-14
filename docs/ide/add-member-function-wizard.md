---
title: Kreator dodawania funkcji członkowskiej
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.function.overview
helpviewer_keywords:
- Add Member Function Wizard [C++]
ms.assetid: 13b6defc-faa6-4d57-83db-9dd854cbea3d
ms.openlocfilehash: eeca957930f125b430ea1a1c6fb1976a07f8fc09
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/10/2018
ms.locfileid: "51519980"
---
# <a name="add-member-function-wizard"></a>Kreator dodawania funkcji członkowskiej

Ten kreator dodaje deklarację funkcji członkowskiej plik nagłówkowy i implementacji funkcji składowej klasy zastępczej pliku implementacji dla wybranej klasy.

Po dodaniu funkcji składowej za pomocą kreatora można edytować kod w środowisku programistycznym.

- **Zwracany typ**

  Ustawia typ zwracany dla funkcji członkowskiej, którego dodajesz. Możesz podać swój własny typ zwracany, lub możesz wybrać z listy dostępnych typów. Aby uzyskać informacje o typach, zobacz [podstawowych typów](../cpp/fundamental-types-cpp.md).

  |            |                   |                   |
  |------------|-------------------|-------------------|
  |  **char**  |      **int**      | **unsigned int**  |
  | **double** |     **long**      | **unsigned long** |
  | **float**  |     **short**     |     **void**      |
  | `HRESULT`  | **unsigned char** |                   |

- **Nazwa funkcji**

  Ustawia nazwę funkcji elementu członkowskiego, który dodajesz.

- **Typ parametru**

  Ustawia typ parametru, którego dodajesz, funkcja elementu członkowskiego, jeśli funkcja elementu członkowskiego ma następujące parametry. Możesz podać swój własny typ parametru, lub możesz wybrać z listy dostępnych typów.

  |            |           |                   |
  |------------|-----------|-------------------|
  |  **char**  |  **int**  | **unsigned char** |
  | **double** | **long**  | **unsigned int**  |
  | **float**  | **short** | **unsigned long** |

- **Nazwa parametru**

  Ustawia nazwę parametru, którego dodajesz, funkcja elementu członkowskiego, jeśli funkcja elementu członkowskiego ma następujące parametry.

- **Lista parametrów**

  Wyświetla listę parametrów, które zostały dodane do funkcji składowej. Aby dodać parametr do listy, podać typ i nazwa w **typ parametru** i **Nazwa parametru** pola i kliknij przycisk **Dodaj**. Aby usunąć parametr z listy, wybierz parametr, a następnie kliknij przycisk **Usuń**.

- **Dostęp do**

  Ustawia dostęp do funkcji składowej. Modyfikatory dostępu są słowami kluczowymi, określające dostęp, innych klas, że funkcja elementu członkowskiego. Zobacz [kontroli dostępu do elementu członkowskiego](../cpp/member-access-control-cpp.md) Aby uzyskać więcej informacji na temat określania dostępu. Poziom dostępu do funkcji elementu członkowskiego jest równa **publicznych** domyślnie.

  - [public](../cpp/public-cpp.md)

  - [protected](../cpp/protected-cpp.md)

  - [private](../cpp/private-cpp.md)

  Sprawdź, czy nowa funkcja elementu członkowskiego jest statyczny lub wirtualnych i czy jest to wbudowane lub czysty. Jeśli ustawisz czysty, funkcji elementu członkowskiego `Virtual` pole wyboru jest zaznaczone oraz **wbudowane** pole staje się niedostępny. Wartością domyślną jest funkcją składową Niestatyczne, niewirtualne.

  | Opcja | Opis |
  |--------|-------------|
  | [Static](../cpp/storage-classes-cpp.md) |  Określa, czy funkcja działa jak globalnym i może być wywołana poza klasy, nawet w przypadku nie tworzenia wystąpienia klasy. Funkcja elementu członkowskiego nie ma dostępu do niestatycznych elementów członkowskich. Funkcja elementu członkowskiego, określony jako `Static` nie może być wirtualny. |
  | [Wirtualny](../cpp/virtual-cpp.md) | Zapewnia, że funkcja poprawny element członkowski jest wywoływana dla obiektu, niezależnie od tego, wyrażenie używane do wywołania funkcji elementu członkowskiego. Funkcja elementu członkowskiego, określony jako `Virtual` nie może być statyczna. |
  | **czyste** | Wskazuje, że nie dostarczono żadnej implementacji dla deklarowanej; funkcja wirtualna elementu członkowskiego w związku z tym **czystej** można określić tylko dla funkcji wirtualnych elementów członkowskich. Klasa, która zawiera co najmniej jeden czystej wirtualnej funkcji składowej jest traktowany jako klasa abstrakcyjna. Klasy pochodne klasy abstrakcyjnej muszą implementować czystej wirtualnej funkcji składowej lub są one zbyt, klasy abstrakcyjne. |
  | [wbudowane](../cpp/inline-functions-cpp.md) | Instruuje kompilator, aby wstawić kopię treści funkcji składowej do każdego miejsca, którego funkcja członkowska jest wywoływana. Funkcja elementu członkowskiego, określony jako **wbudowane** nie może być czysty. |

- **Plik CPP**

  Ustawia lokalizację pliku, w którym zapisywana jest implementacja funkcji składowej klasy zastępczej. Domyślnie jest ona zapisywana w pliku .cpp dla klasy, do którego jest dodawana funkcja elementu członkowskiego. Kliknij przycisk wielokropka, aby zmienić nazwę pliku. Implementacja funkcji elementu członkowskiego jest dodawany do zawartość wybranego pliku.

- **Komentarz**

  Zawiera komentarz w pliku nagłówkowym dla funkcji członkowskiej.

- **Sygnatura funkcji**

  Wyświetla funkcja elementu członkowskiego, jak wygląda na to, w kodzie po kliknięciu **Zakończ**. Nie można edytować tekst w tym polu. Aby zmienić funkcja elementu członkowskiego, należy zmienić odpowiednie pola w kreatorze.

## <a name="see-also"></a>Zobacz też

[Dodawanie funkcji członkowskiej](../ide/adding-a-member-function-visual-cpp.md)