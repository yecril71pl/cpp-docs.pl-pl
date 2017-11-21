---
title: "/Zc:throwingNew (zgłasza nowy operator Przyjmij) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 12/13/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- throwingNew
- /Zc:throwingNew
dev_langs: C++
helpviewer_keywords:
- -Zc compiler options (C++)
- throwingNew
- Assume operator new Throws
- /Zc compiler options (C++)
- Zc compiler options (C++)
ms.assetid: 20ff0101-9677-4d83-8c7b-8ec9ca49f04f
caps.latest.revision: "1"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: bc784af1c23576ff68c8be8b4b400cd10cc8b0e2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="zcthrowingnew-assume-operator-new-throws"></a>/Zc:throwingNew (Przyjmij zgłasza nowy operator)  
Gdy `/Zc:throwingNew` zostanie określona opcja, kompilator optymalizuje wywołań `operator new` pomijania sprawdzania dla wskaźnika o wartości null zwracane. Ta opcja nakazuje kompilatorowi założono, że wszystkie połączone implementacje `operator new` i niestandardowych allocators — są zgodne ze standardem C++ i zgłosić na błąd alokacji. Domyślnie w programie Visual Studio, kompilator generuje pessimistically sprawdzenia wartości null (`/Zc:throwingNew-`) dla tych wywołuje, ponieważ użytkownicy można połączyć z systemem innym niż zgłaszanie implementacji `operator new` lub zapisu procedur przydzielania niestandardowych, które zwraca wskaźniki o wartości null.  
  
## <a name="syntax"></a>Składnia  
  
`/Zc:throwingNew`[`-`]  
  
## <a name="remarks"></a>Uwagi  
  
Od ISO języka C ++ 98 standardowego została określona, która domyślnie [nowy operator](../../standard-library/new-operators.md#op_new) zgłasza `std::bad_alloc` Jeśli alokacja pamięci nie powiodło się. Wersje Visual C++ do programu Visual Studio 6.0 zwrócił wskaźnika o wartości null na błąd alokacji. W programie Visual Studio 2002 `operator new` zgodne ze standardem i zgłoszenie błędu. Do obsługi kodu, który używa starszej stylu alokacji, Visual Studio udostępnia implementację możliwym `operator new` w *nothrownew.obj* zwracającą wskaźnika o wartości null w przypadku awarii. Domyślnie kompilator generuje obrony sprawdzenia wartości null, aby zapobiec tych starszych allocators — powoduje natychmiastowe awarii w przypadku awarii. `/Zc:throwingNew` Opcja nakazuje kompilatorowi Opuść te sprawdzenia wartości null, przy założeniu, że wszystkie połączone pamięci allocators — jest zgodna ze standardem. Nie dotyczy to jawne z systemem innym niż wyrzucające `operator new` przeciążenia, które są zadeklarowane za pomocą dodatkowy parametr typu `std::nothrow_t` i mieć jawnego `noexcept` specyfikacji.  
  
Koncepcyjnie, do utworzenia obiektu w magazynie bezpłatne, kompilator generuje kod, aby przydzielić pamięci, a następnie wywołać jej konstruktora w celu zainicjowania pamięć. Ponieważ kompilatora Visual C++ zwykle nie wiadomo, ten kod będzie połączona z alokatora niezgodnych, zgłaszanie, domyślnie generowany jest również sprawdzania wartości null przed wywołaniem konstruktora. Zapobiega to pustego wskaźnika wyłuskania w wywołaniu konstruktora, jeśli alokację zgłaszanie nie powiedzie się. W większości przypadków te testy są zbędne, ponieważ domyślny `operator new` allocators — throw zamiast zwracać wskaźniki o wartości null. Kontrole ma także niefortunne efekty uboczne. One wybrzuszanie rozmiar kodu, ich wypełniania predykcyjne gałęzi i ich wstrzymywania inne optymalizacje kompilatora przydatne, takie jak devirtualization lub const propagacji poza zainicjowanego obiektu. Sprawdza obecność tylko do obsługi kodu, który stanowi łącze do *nothrownew.obj* lub ma niestandardowy niezgodnych `operator new` implementacji. Jeśli nie używasz niezgodnych `operator new`, zalecane jest użycie `/Zc:throwingNew` optymalizacji kodu.  
  
Jeśli kompilacja przy użyciu Generowanie łączonych kodów czasowych (LTCG), nie trzeba określić `/Zc:throwingNew`. Podczas kompilowania kodu za pomocą LTCG kompilator może wykryć, czy wartość domyślna zgodnych `operator new` implementacji jest używany. Jeśli tak, kompilator powoduje, że sprawdzenia wartości null automatycznie. Wyszukuje konsolidator `/ThrowingNew` flagę, aby sprawdzić, czy wdrożenia `operator new` jest zgodny. Ta flaga do konsolidatora można określić przez dołączenie tej dyrektywy w źródle implementacji nowego operatora niestandardowego:  
  
```cpp  
#pragma comment(linker, "/ThrowingNew")  
```  
  
Aby uzyskać więcej informacji na temat problemów zgodności w programie Visual C++, zobacz [niestandardowe zachowanie](../../cpp/nonstandard-behavior.md).  
  
## <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).  
2.  Z **konfiguracje** rozwijane menu, wybierz **wszystkie konfiguracje**.  
3.  Wybierz **właściwości konfiguracji**, **C/C++**, **wiersza polecenia** strony właściwości.  
4.  Modyfikowanie **dodatkowe opcje** właściwości, aby uwzględnić `/Zc:throwingNew` lub `/Zc:throwingNew-` , a następnie wybierz **OK**.  
  
## <a name="see-also"></a>Zobacz też  
[Opcje kompilatora](../../build/reference/compiler-options.md)  
[Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)  
[/Zc (zgodność)](../../build/reference/zc-conformance.md)  
[noexcept (C++)](../../cpp/noexcept-cpp.md)  
[Specyfikacje wyjątków (throw) (C++)](../../cpp/exception-specifications-throw-cpp.md)  
[Zakończenie (wyjątek)](../../standard-library/exception-functions.md#terminate)  
