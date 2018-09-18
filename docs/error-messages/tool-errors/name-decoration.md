---
title: Nazwij Dekorację | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/05/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
dev_langs:
- C++
helpviewer_keywords:
- name decoration [C++]
- names [C++], decorated
- decorated names, calling conventions
ms.assetid: 8327a27b-bb4f-49f2-8218-b851b9d2a463
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fa493a886509a85cc45c14f003ff07886c435280
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46036036"
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

## <a name="see-also"></a>Zobacz też

[Błąd narzędzi konsolidatora LNK2001](../../error-messages/tool-errors/linker-tools-error-lnk2001.md)