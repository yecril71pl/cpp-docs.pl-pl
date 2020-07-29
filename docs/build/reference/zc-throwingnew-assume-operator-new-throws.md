---
title: /Zc:throwingNew (Przyjmowanie nowych zgłoszeń operatora)
ms.date: 03/01/2018
f1_keywords:
- throwingNew
- /Zc:throwingNew
helpviewer_keywords:
- -Zc compiler options (C++)
- throwingNew
- Assume operator new Throws
- /Zc compiler options (C++)
- Zc compiler options (C++)
ms.assetid: 20ff0101-9677-4d83-8c7b-8ec9ca49f04f
ms.openlocfilehash: 7593107a280995145d252efa76e0a88bddbd2275
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87211869"
---
# <a name="zcthrowingnew-assume-operator-new-throws"></a>/Zc:throwingNew (Przyjmowanie nowych zgłoszeń operatora)

Gdy określona jest opcja **/Zc: throwingNew** , kompilator optymalizuje wywołania do `operator new` , aby pominąć testy dla zwracanego wskaźnika o wartości null. Ta opcja nakazuje kompilatorowi założenie, że wszystkie połączone implementacje `operator new` i niestandardowe przydziały są zgodne ze standardem C++ i throw przy błędzie alokacji. Domyślnie w programie Visual Studio kompilator pessimistically generuje sprawdzanie wartości null (**/Zc: throwingNew-**) dla tych wywołań, ponieważ użytkownicy mogą łączyć się z niezgłaszaną implementacją `operator new` lub pisać niestandardowe procedury alokatora, które zwracają wskaźniki o wartości null.

## <a name="syntax"></a>Składnia

> **/Zc: throwingNew**[ **-** ]

## <a name="remarks"></a>Uwagi

Ze względu na to, że ISO C++ 98, standard określił, że domyślny [operator new](../../standard-library/new-operators.md#op_new) zgłasza, `std::bad_alloc` gdy alokacja pamięci nie powiedzie się. Wersje Visual C++ do programu Visual Studio 6,0 zwróciły wskaźnik o wartości null dotyczący błędu alokacji. Począwszy od programu Visual Studio 2002, `operator new` jest zgodna ze standardem i zgłasza błąd. Aby można było obsługiwać kod, który używa starszego stylu alokacji, program Visual Studio udostępnia implementację `operator new` w nothrownew. obj, która zwraca wskaźnik o wartości null w przypadku niepowodzenia. Domyślnie kompilator generuje również obronną kontrolę wartości null, aby zapobiec występowaniu natychmiastowej awarii w przypadku niepowodzenia. Opcja **/Zc: throwingNew** instruuje kompilator, aby opuścił te sprawdzenia wartości null, w założeniu, że wszystkie połączone przystawki pamięci są zgodne ze standardem. Nie dotyczy to jawnych `operator new` przeciążeń, które są zadeklarowane przy użyciu dodatkowego parametru typu `std::nothrow_t` i mają jawną **`noexcept`** specyfikację.

Koncepcyjnie, aby utworzyć obiekt w wolnym magazynie, kompilator generuje kod w celu przydzielenia pamięci, a następnie wywołania konstruktora w celu zainicjowania pamięci. Ponieważ kompilator MSVC zazwyczaj nie może stwierdzić, czy ten kod będzie połączony z niezgodnym, niezgłaszanym alokatorem, domyślnie generuje także sprawdzenie wartości null przed wywołaniem konstruktora. Zapobiega to dereferencji wskaźnika NULL w wywołaniu konstruktora, jeśli niezgłaszane alokacje nie powiedzie się. W większości przypadków te testy są niepotrzebne, ponieważ domyślne przystawcy są zwracane `operator new` zamiast zwracać wskaźniki o wartości null. Sprawdzenia również mają niezbyt szczęście skutki uboczne. Przeładowanie rozmiar kodu, zalewają predykcyjność gałęzi i zablokują inne przydatne optymalizacje kompilatora, takie jak dewirtualizacja lub Propagacja stała z zainicjowanego obiektu. Testy istnieją tylko w przypadku obsługi kodu, który łączy się z *nothrownew. obj* lub ma niestandardowe `operator new` implementacje niezgodne. Jeśli nie korzystasz z niezgodności `operator new` , zalecamy użycie **/Zc: throwingNew** w celu zoptymalizowania kodu.

Opcja **/Zc: throwingNew** jest domyślnie wyłączona i nie dotyczy opcji [/permissive-](permissive-standards-conformance.md) .

Jeśli kompilujesz przy użyciu generowania kodu w czasie konsolidacji (LTCG), nie musisz określać **/Zc: throwingNew**. Gdy kod jest kompilowany przy użyciu LTCG, kompilator może wykryć, czy `operator new` jest używana domyślna implementacja zgodna z implementacją. Jeśli tak, kompilator pozostawia sprawdzanie wartości null automatycznie. Konsolidator wyszukuje flagę **/ThrowingNew** , aby stwierdzić, czy implementacja `operator new` jest zgodna. Możesz określić tę flagę dla konsolidatora, dołączając tę dyrektywę w źródle dla niestandardowej implementacji operatora:

```cpp
#pragma comment(linker, "/ThrowingNew")
```

Aby uzyskać więcej informacji na temat problemów ze zgodnością w Visual C++, zobacz [niestandardowe zachowanie](../../cpp/nonstandard-behavior.md).

## <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz okno dialogowe **strony właściwości** projektu. Aby uzyskać szczegółowe informacje, zobacz [Ustawianie kompilatora C++ i właściwości kompilacji w programie Visual Studio](../working-with-project-properties.md).

1. Z menu rozwijanego **Konfiguracja** wybierz pozycję **wszystkie konfiguracje**.

1. Wybierz **Configuration Properties**  >  stronę właściwości konfiguracja wiersza polecenia**C/C++**  >  **Command Line** .

1. Zmodyfikuj właściwość **Opcje dodatkowe** , aby uwzględnić **/Zc: throwingNew** lub **/Zc: throwingNew-** , a następnie wybierz **przycisk OK**.

## <a name="see-also"></a>Zobacz także

[Opcje kompilatora MSVC](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)<br/>
[/Zc (Zgodność)](zc-conformance.md)<br/>
[noexcept (C++)](../../cpp/noexcept-cpp.md)<br/>
[Specyfikacje wyjątków (throw) (C++)](../../cpp/exception-specifications-throw-cpp.md)<br/>
[Przerwij (wyjątek)](../../standard-library/exception-functions.md#terminate)<br/>
