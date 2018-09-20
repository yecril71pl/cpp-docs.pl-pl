---
title: Tablica parametrów i wielokropek | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- function overloading, argument matching
ms.assetid: 492e3f6c-1c4c-4e0c-a358-72f2d39c30be
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 2caf6415fdbceb506b736e209c6e7e384b567c5a
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46384380"
---
# <a name="param-array-and-ellipsis"></a>Tablica parametrów i wielokropek

Pierwszeństwo Tablica parametrów wywołania przeciążonych funkcji rozpoznawania zmienił się z zarządzanych rozszerzeń języka C++ do Visual C++.

Zarówno w przypadku zarządzanych rozszerzeń, jak i Nowa składnia nie jest jawną obsługiwane dla Tablica parametrów, który obsługuje C# i Visual Basic. Zamiast tego jednego flagi zwykłych tablicy za pomocą atrybutu w następujący sposób:

```
void Trace1( String* format, [ParamArray]Object* args[] );
void Trace2( String* format, Object* args[] );
```

Gdy zarówno wyglądają tak samo, `ParamArray` atrybut tagi to dla języka C# lub innych języków CLR jako tablicę, biorąc zmienną liczbę elementów przy każdym wywołaniu. Zmiany w zachowaniu w programach między zarządzanych rozszerzeń i nowej składni znajduje się w rozdzielczości przeciążonej funkcji, w których jedno wystąpienie deklaruje wielokropek i deklaruje sekundy `ParamArray` atrybutu, jak w poniższym przykładzie, dostarczone przez Artur Laksberg.

```
int fx(...); // 1
int fx( [ParamArray] Int32[] ); // 2
```

W zarządzanych rozszerzeń wielokropka został pierwszeństwo przed atrybut, który jest uzasadnione, ponieważ ten atrybut nie ma formalnych aspektów języka. Jednak w nowej składni Tablica parametrów jest teraz obsługiwany bezpośrednio z poziomu języka i jest mu nadawana pierwszeństwo na wielokropek, ponieważ jest bardziej silnie typizowane. W związku z tym w wywołaniu zarządzanych rozszerzeń

```
fx( 1, 2 );
```

jest rozpoznawana jako `fx(...)` znajduje się w nowej składni, jest on rozpoznawany jako `ParamArray` wystąpienia. Na wyłączone ryzyko, że Twoje zachowanie programu zależy od wywołania wystąpienia wielokropka porównaniu z `ParamArray`, musisz zmodyfikować podpis lub wywołanie.

## <a name="see-also"></a>Zobacz też

[Ogólne zmiany w języku (C++/CLI)](../dotnet/general-language-changes-cpp-cli.md)