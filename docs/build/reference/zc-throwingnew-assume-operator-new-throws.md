---
title: /Zc:throwingNew (przyjmowanie zgłasza nowy operator)
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
ms.openlocfilehash: c8c7b4e7246cc3bb1b3a73cde4f6830eb7178dd2
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57813516"
---
# <a name="zcthrowingnew-assume-operator-new-throws"></a>/Zc:throwingNew (przyjmowanie zgłasza nowy operator)

Gdy **/Zc:throwingNew** opcja zostanie określona, kompilator optymalizuje wywołania `operator new` do pominięcia sprawdza, czy zwracany wskaźnik o wartości null. Ta opcja informuje kompilator, aby założył, że wszystkie połączone implementacje `operator new` i niestandardowych alokatorów są zgodne ze standardem C++ i po niepowodzeniu alokacji. Domyślnie w programie Visual Studio, kompilator generuje pessimistically sprawdzanie wartości null (**/Zc:throwingNew-**) dla tych wywołań, ponieważ użytkownicy mogą tworzyć połączenia z implementacją niezgłaszające z `operator new` lub napisać niestandardowy alokator procedury które zwracają wskaźników o wartości null.

## <a name="syntax"></a>Składnia

> **/Zc:throwingNew**[**-**]

## <a name="remarks"></a>Uwagi

Od czasu ISO C ++ 98 standard została określona, domyślnie [nowy operator](../../standard-library/new-operators.md#op_new) zgłasza `std::bad_alloc` Jeśli alokacja pamięci nie powiedzie się. Wystąpił błąd alokacji wersji programu Visual C++ do Visual Studio 6.0 zwrócona wskaźnikiem typu null. Począwszy od programu Visual Studio 2002, `operator new` jest zgodny ze standardem i zgłoszenie błędu. Do obsługi kodu, który używa starszego stylu alokacji, program Visual Studio udostępnia możliwym implementacji `operator new` w nothrownew.obj, która zwraca wskaźnik o wartości null w przypadku niepowodzenia. Domyślnie kompilator generuje obrony sprawdzanie wartości null, aby uniemożliwić powoduje natychmiastowe awarii w przypadku niepowodzenia tych buforów starszym stylu. **/Zc:throwingNew** opcji informuje kompilator, aby pozostawić te kontrole wartości null, przy założeniu, że wszystkie połączone pamięci puli buforów jest zgodna ze standardem. Dotyczy to jawne niezgłaszające `operator new` przeciążeń, które są zadeklarowane za pomocą dodatkowy parametr typu `std::nothrow_t` i mieć jawnego `noexcept` specyfikacji.

Model do utworzenia obiektu w wolnym magazynie, kompilator generuje kod, aby przydzielić pamięci a następnie wywołać jej konstruktora można zainicjować pamięci. Ponieważ kompilator MSVC zwykle nie wiadomo, ten kod będzie połączona z alokatora niezgodnych, niezgłaszające, domyślnie generuje również sprawdzanie wartości null, przed wywołaniem konstruktora. Zapobiega to pustego wskaźnika cofnięcia odwołania w wywołaniu konstruktora, jeśli niezgłaszające alokacja nie powiedzie się. W większości przypadków te testy są zbędne, ponieważ wartość domyślna `operator new` buforów throw zamiast zwracać wskaźników o wartości null. Kontrole również mieć niefortunne efekty uboczne. One wybrzuszanie rozmiar kodu, ich zalać predykcyjne gałęzi i ich wstrzymywania inne optymalizacje kompilatora użyteczne, takie jak devirtualization lub const propagacji poza zainicjowanego obiektu. Sprawdza obecność tylko do obsługi kodu, który stanowi łącze do *nothrownew.obj* lub niestandardowe niezgodnych `operator new` implementacji. Jeśli nie używasz niezgodnych `operator new`, zalecamy użycie **/Zc:throwingNew** optymalizacji kodu.

**/Zc:throwingNew** opcja jest domyślnie wyłączona i nie ma wpływu [/ permissive-](permissive-standards-conformance.md) opcji.

Jeśli kompilujesz przy użyciu generowanie kodu w czasie konsolidowania (LTCG), nie należy określić **/Zc:throwingNew**. Gdy kod jest kompilowany przy użyciu LTCG, kompilator może wykryć, jeśli wartość domyślna zgodnych `operator new` implementacja jest używana. Jeśli tak, kompilator powoduje, że sprawdzenia wartości null automatycznie. Konsolidator szuka **/ThrowingNew** flagę, aby sprawdzić, jeśli implementacja `operator new` jest zgodny. Należy określić tej flagi konsolidatora, umieszczając tej dyrektywy w źródle, implementacji nowych niestandardowy operator:

```cpp
#pragma comment(linker, "/ThrowingNew")
```

Aby uzyskać więcej informacji na temat problemów ze zgodnością w języku Visual C++, zobacz [niestandardowe zachowanie](../../cpp/nonstandard-behavior.md).

## <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. Z **konfiguracji** menu rozwijanym, wybierz polecenie **wszystkie konfiguracje**.

1. Wybierz **właściwości konfiguracji** > **C/C++** > **wiersza polecenia** stronę właściwości.

1. Modyfikowanie **dodatkowe opcje** właściwości do uwzględnienia **/Zc:throwingNew** lub **/Zc:throwingNew-** , a następnie wybierz **OK**.

## <a name="see-also"></a>Zobacz także

[MSVC Compiler Options](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)<br/>
[/Zc (Zgodność)](zc-conformance.md)<br/>
[noexcept (C++)](../../cpp/noexcept-cpp.md)<br/>
[Specyfikacje wyjątków (throw) (C++)](../../cpp/exception-specifications-throw-cpp.md)<br/>
[Zakończenie (wyjątku)](../../standard-library/exception-functions.md#terminate)<br/>
