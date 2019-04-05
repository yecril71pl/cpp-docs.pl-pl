---
title: Nazwij dekorację
ms.date: 09/05/2018
helpviewer_keywords:
- name decoration [C++]
- names [C++], decorated
- decorated names, calling conventions
ms.assetid: 8327a27b-bb4f-49f2-8218-b851b9d2a463
ms.openlocfilehash: b916a73e0b8f86755384914fa85ef8a901e4a64c
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "59041526"
---
# <a name="name-decoration"></a>Nazwij dekorację

Nazwij dekorację zazwyczaj odwołuje się do konwencji nazewnictwa języka C++, ale można zastosować do wielu przypadków C, jak również. Domyślnie C++ używa nazwy funkcji, parametry oraz zwracany typ do utworzenia konsolidatora nazwy funkcji. Rozważmy następującą funkcję:

```
void CALLTYPE test(void)
```

W poniższej tabeli przedstawiono nazwy konsolidatora dla różnych konwencji wywoływania.

|Konwencja wywoływania|extern "C" lub .c pliku|.cpp, .cxx lub /TP|
|------------------------|---------------------------|------------------------|
|Konwencja nazewnictwa języka C (`__cdecl`)|`_test`|`?test@@ZAXXZ`|
|Konwencja nazewnictwa Fastcall (`__fastcall`)|`@test@0`|`?test@@YIXXZ`|
|Standardowej konwencji nazewnictwa wywołania (`__stdcall`)|`_test@0`|`?test@@YGXXZ`|
|Konwencja nazewnictwa Vectorcall (`__vectorcall`)|`test@@0`|`?test@@YQXXZ`|

Extern "C" umożliwia wywoływanie funkcji C z języka C++. Extern "C" wymusza korzystanie z języka C Konwencja nazewnictwa dla funkcji języka C++ klasy korporacyjnej. Należy pamiętać o przełączniki kompilatora **TP** lub **/Tp**, które nakazuje kompilatorowi ignorowanie rozszerzenie nazwy pliku i skompiluj plik jako C lub C++, odpowiednio. Te opcje mogą powodować nazwy, które nie oczekuje.

Posiadanie prototypy funkcji, które mają niezgodne parametry może spowodować błąd. Nazwij dekorację dołącza parametry funkcji do końcowego funkcji dekorowane nazwy. Wywołanie funkcji z typami parametrów, które nie odpowiadają wartościom w deklaracji funkcji może spowodować LNK2001.

Nie istnieje obecnie standard c++ nazewnictwa między dostawcami kompilatora lub nawet między różnymi wersjami kompilatora. W związku z tym konsolidacji plików obiektu skompilowany za pomocą innych kompilatorów nie może utworzyć ten sam schemat nazewnictwa i w związku z tym powoduje, że nierozpoznane obiekty zewnętrzne.

## <a name="see-also"></a>Zobacz także

[Błąd narzędzi konsolidatora LNK2001](../../error-messages/tool-errors/linker-tools-error-lnk2001.md)