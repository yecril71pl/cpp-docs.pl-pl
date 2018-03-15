---
title: "/Zc:throwingNew (zgłasza nowy operator Przyjmij) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 03/01/2018
ms.technology:
- cpp-tools
ms.topic: article
f1_keywords:
- throwingNew
- /Zc:throwingNew
dev_langs:
- C++
helpviewer_keywords:
- -Zc compiler options (C++)
- throwingNew
- Assume operator new Throws
- /Zc compiler options (C++)
- Zc compiler options (C++)
ms.assetid: 20ff0101-9677-4d83-8c7b-8ec9ca49f04f
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: cc29a364e5001fb319017a1bc2fa084514d52f16
ms.sourcegitcommit: eeb2b5ad8d3d22514a7b9bd7d756511b69ae0ccf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2018
---
# <a name="zcthrowingnew-assume-operator-new-throws"></a>/Zc:throwingNew (Przyjmij zgłasza nowy operator)

Gdy **/Zc:throwingNew** zostanie określona opcja, kompilator optymalizuje wywołań `operator new` pomijania sprawdzania dla wskaźnika o wartości null zwracane. Ta opcja nakazuje kompilatorowi założono, że wszystkie połączone implementacje `operator new` i niestandardowych allocators — są zgodne ze standardem C++ i zgłosić na błąd alokacji. Domyślnie w programie Visual Studio, kompilator generuje pessimistically sprawdzenia wartości null (**/Zc:throwingNew-**) dla tych wywołuje, ponieważ użytkownicy można połączyć z systemem innym niż zgłaszanie implementacji `operator new` lub zapisu alokatora niestandardowe procedury wskaźniki o wartości null, które zwracają.

## <a name="syntax"></a>Składnia

> **/Zc:throwingNew**[**-**]

## <a name="remarks"></a>Uwagi

Od ISO języka C ++ 98 standardowego została określona, która domyślnie [nowy operator](../../standard-library/new-operators.md#op_new) zgłasza `std::bad_alloc` Jeśli alokacja pamięci nie powiodło się. Wersje Visual C++ do programu Visual Studio 6.0 zwrócił wskaźnika o wartości null na błąd alokacji. W programie Visual Studio 2002 `operator new` zgodne ze standardem i zgłoszenie błędu. Do obsługi kodu, który używa starszej stylu alokacji, Visual Studio udostępnia implementację możliwym `operator new` w nothrownew.obj, która zwraca wskaźnika o wartości null w przypadku awarii. Domyślnie kompilator generuje obrony sprawdzenia wartości null, aby zapobiec tych starszych allocators — powoduje natychmiastowe awarii w przypadku awarii. **/Zc:throwingNew** opcja nakazuje kompilatorowi Opuść te sprawdzenia wartości null, przy założeniu, że wszystkie połączone pamięci allocators — jest zgodna ze standardem. Nie dotyczy to jawne z systemem innym niż wyrzucające `operator new` przeciążenia, które są zadeklarowane za pomocą dodatkowy parametr typu `std::nothrow_t` i mieć jawnego `noexcept` specyfikacji.

Koncepcyjnie, do utworzenia obiektu w magazynie bezpłatne, kompilator generuje kod, aby przydzielić pamięci, a następnie wywołać jej konstruktora w celu zainicjowania pamięć. Ponieważ kompilatora Visual C++ zwykle nie wiadomo, ten kod będzie połączona z alokatora niezgodnych, zgłaszanie, domyślnie generowany jest również sprawdzania wartości null przed wywołaniem konstruktora. Zapobiega to pustego wskaźnika wyłuskania w wywołaniu konstruktora, jeśli alokację zgłaszanie nie powiedzie się. W większości przypadków te testy są zbędne, ponieważ domyślny `operator new` allocators — throw zamiast zwracać wskaźniki o wartości null. Kontrole ma także niefortunne efekty uboczne. One wybrzuszanie rozmiar kodu, ich wypełniania predykcyjne gałęzi i ich wstrzymywania inne optymalizacje kompilatora przydatne, takie jak devirtualization lub const propagacji poza zainicjowanego obiektu. Sprawdza obecność tylko do obsługi kodu, który stanowi łącze do *nothrownew.obj* lub ma niestandardowy niezgodnych `operator new` implementacji. Jeśli nie używasz niezgodnych `operator new`, zalecane jest użycie **/Zc:throwingNew** optymalizacji kodu.

**/Zc:throwingNew** opcja jest domyślnie wyłączona i nie ma wpływu na [/ ograniczająca-](permissive-standards-conformance.md) opcji.

Jeśli kompilacja przy użyciu Generowanie łączonych kodów czasowych (LTCG), nie trzeba określić **/Zc:throwingNew**. Podczas kompilowania kodu za pomocą LTCG kompilator może wykryć, czy wartość domyślna zgodnych `operator new` implementacji jest używany. Jeśli tak, kompilator powoduje, że sprawdzenia wartości null automatycznie. Wyszukuje konsolidator **/ThrowingNew** flagę, aby sprawdzić, czy wdrożenia `operator new` jest zgodny. Ta flaga do konsolidatora można określić przez dołączenie tej dyrektywy w źródle implementacji nowego operatora niestandardowego:

```cpp
#pragma comment(linker, "/ThrowingNew")
```

Aby uzyskać więcej informacji na temat problemów zgodności w programie Visual C++, zobacz [niestandardowe zachowanie](../../cpp/nonstandard-behavior.md).

## <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. Z **konfiguracji** rozwijane menu, wybierz **wszystkie konfiguracje**.

1. Wybierz **właściwości konfiguracji** > **C/C++** > **wiersza polecenia** strony właściwości.

1. Modyfikowanie **dodatkowe opcje** właściwości, aby uwzględnić **/Zc:throwingNew** lub **/Zc:throwingNew-** , a następnie wybierz **OK**.

## <a name="see-also"></a>Zobacz także

[Opcje kompilatora](../../build/reference/compiler-options.md)<br/>
[Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)<br/>
[/Zc (Zgodność)](../../build/reference/zc-conformance.md)<br/>
[noexcept (C++)](../../cpp/noexcept-cpp.md)<br/>
[Specyfikacje wyjątków (throw) (C++)](../../cpp/exception-specifications-throw-cpp.md)<br/>
[Zakończenie (wyjątek)](../../standard-library/exception-functions.md#terminate)<br/>
