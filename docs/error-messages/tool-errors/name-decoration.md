---
title: Nazwij dekorację
ms.date: 04/22/2019
helpviewer_keywords:
- name decoration [C++]
- names [C++], decorated
- decorated names, calling conventions
ms.assetid: 8327a27b-bb4f-49f2-8218-b851b9d2a463
ms.openlocfilehash: d1557f53a07a544ff4f9e5a63f905e6854fb74ce
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62393158"
---
# <a name="name-decoration"></a>Nazwij dekorację

Nazwij dekorację zazwyczaj odwołuje się do konwencji nazewnictwa języka C++, ale można zastosować do wielu przypadków C, jak również. Domyślnie C++ używa nazwy funkcji, parametry oraz zwracany typ do utworzenia konsolidatora nazwy funkcji. Rozważmy następującą deklarację funkcji:

`void CALLTYPE test(void);`

W poniższej tabeli przedstawiono nazwy konsolidatora dla różnych konwencji wywoływania.

|Konwencja wywoływania|`extern "C"` lub `.c` pliku|`.cpp`, `.cxx` lub `/TP`|
|------------------------|---------------------------|------------------------|
|Konwencja nazewnictwa języka C (`__cdecl`)|`_test`|`?test@@ZAXXZ`|
|Szybkie wywołanie konwencji nazewnictwa (`__fastcall`)|`@test@0`|`?test@@YIXXZ`|
|Standardowe wywołanie konwencji nazewnictwa (`__stdcall`)|`_test@0`|`?test@@YGXXZ`|
|Vector konwencją wywołania (`__vectorcall`)|`test@@0`|`?test@@YQXXZ`|

Użyj `extern "C"` do wywoływania funkcji języka C z C++. `extern "C"` wymusza użycie języka C Konwencja nazewnictwa dla klasy korporacyjnej C++ funkcji. Należy pamiętać o przełączniki kompilatora **TP** lub **/Tp**, które nakazuje kompilatorowi ignorowanie rozszerzenie nazwy pliku i skompiluj plik jako C lub C++, odpowiednio. Te opcje mogą powodować nazwy konsolidatora, które nie będą raczej.

Posiadanie prototypy funkcji, które mają niezgodne parametry może spowodować błąd. Nazwij dekorację dołącza parametry funkcji do końcowego funkcji dekorowane nazwy. Wywołanie funkcji z typami parametrów, które nie odpowiadają wartościom w deklaracji funkcji może spowodować LNK2001.

Obecnie nie istnieją standardy dla C++ nazewnictwa między dostawcami kompilatora lub nawet między różnymi wersjami kompilatora. Łączenie plików obiektów skompilowany przez inne kompilatory nie może utworzyć ten sam schemat nazewnictwa i może powodować nierozpoznane obiekty zewnętrzne.

## <a name="see-also"></a>Zobacz także

[Błąd narzędzi konsolidatora LNK2001](../../error-messages/tool-errors/linker-tools-error-lnk2001.md)