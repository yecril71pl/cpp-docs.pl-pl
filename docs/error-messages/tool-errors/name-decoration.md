---
title: Nazwij dekorację
ms.date: 04/22/2019
helpviewer_keywords:
- name decoration [C++]
- names [C++], decorated
- decorated names, calling conventions
ms.assetid: 8327a27b-bb4f-49f2-8218-b851b9d2a463
ms.openlocfilehash: 6a43b952b2f8f9bcbb5e835bf8e20682c99f2935
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87218042"
---
# <a name="name-decoration"></a>Nazwij dekorację

Dekoracja nazw zazwyczaj odnosi się do konwencji nazewnictwa języka C++, ale może być również stosowana do wielu przypadków C. Domyślnie C++ używa nazwy funkcji, parametrów i zwracanego typu, aby utworzyć nazwę konsolidatora dla funkcji. Rozważmy następującą deklarację funkcji:

`void CALLTYPE test(void);`

W poniższej tabeli przedstawiono nazwę konsolidatora dla różnych konwencji wywoływania.

|Konwencja wywoływania|`extern "C"``.c`plik lub|`.cpp``.cxx`lub`/TP`|
|------------------------|---------------------------|------------------------|
|Konwencja nazewnictwa języka C ( **`__cdecl`** )|`_test`|`?test@@ZAXXZ`|
|Konwencja nazewnictwa szybkiego wywołania ( **`__fastcall`** )|`@test@0`|`?test@@YIXXZ`|
|Standardowa Konwencja nazewnictwa wywołań ( **`__stdcall`** )|`_test@0`|`?test@@YGXXZ`|
|Konwencja nazewnictwa wywołań wektorowych ( **`__vectorcall`** )|`test@@0`|`?test@@YQXXZ`|

Użyj `extern "C"` , aby wywołać funkcję C z języka C++. `extern "C"`wymusza użycie konwencji nazewnictwa języka C dla funkcji niebędących klasami C++. Należy pamiętać o przełącznikach kompilatora **/TC** lub **/TP**, które informują kompilator, aby ignorował rozszerzenie nazwy pliku i kompilować plik odpowiednio w języku C lub C++. Te opcje mogą spowodować nieoczekiwane nazwy konsolidatora.

W przypadku prototypów funkcji, które mają niezgodne parametry, może być również przyczyną tego błędu. Dekoracja nazwy obejmuje parametry funkcji w końcowej nazwie funkcji dekoracyjnej. Wywołanie funkcji z typami parametrów, które nie pasują do tych w deklaracji funkcji, może również spowodować LNK2001.

Obecnie nie ma żadnych standardów nazewnictwa C++ między dostawcami kompilatora, a nawet między różnymi wersjami kompilatora. Łączenie plików obiektów skompilowanych przez inne kompilatory może nie dawać tego samego schematu nazewnictwa i może powodować nierozpoznane zewnętrzne.

## <a name="see-also"></a>Zobacz także

[LNK2001 błędu narzędzi konsolidatora](../../error-messages/tool-errors/linker-tools-error-lnk2001.md)
