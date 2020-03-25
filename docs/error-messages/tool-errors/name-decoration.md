---
title: Nazwij dekorację
ms.date: 04/22/2019
helpviewer_keywords:
- name decoration [C++]
- names [C++], decorated
- decorated names, calling conventions
ms.assetid: 8327a27b-bb4f-49f2-8218-b851b9d2a463
ms.openlocfilehash: cc00c971eac2a089ccec5bd9eab594bdf4e8348e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80173520"
---
# <a name="name-decoration"></a>Nazwij dekorację

Dekoracja nazw zazwyczaj odnosi się do C++ konwencji nazewnictwa, ale może być również stosowana do wielu przypadków C. Domyślnie program C++ używa nazwy funkcji, parametrów i typu zwracanego, aby utworzyć nazwę konsolidatora dla funkcji. Rozważmy następującą deklarację funkcji:

`void CALLTYPE test(void);`

W poniższej tabeli przedstawiono nazwę konsolidatora dla różnych konwencji wywoływania.

|Konwencja wywoływania|plik `extern "C"` lub `.c`|`.cpp`, `.cxx` lub `/TP`|
|------------------------|---------------------------|------------------------|
|Konwencja nazewnictwa języka C (`__cdecl`)|`_test`|`?test@@ZAXXZ`|
|Konwencja nazewnictwa szybkiego wywołania (`__fastcall`)|`@test@0`|`?test@@YIXXZ`|
|Standardowa Konwencja nazewnictwa wywołań (`__stdcall`)|`_test@0`|`?test@@YGXXZ`|
|Konwencja nazewnictwa wywołań wektorowych (`__vectorcall`)|`test@@0`|`?test@@YQXXZ`|

Użyj `extern "C"`, aby wywołać funkcję C z C++. `extern "C"` wymusza użycie konwencji nazewnictwa języka C dla funkcji niebędących klasami C++ . Należy pamiętać o przełącznikach kompilatora **/TC** lub **/TP**, które poinformują kompilator, aby ignorował rozszerzenie nazwy pliku i kompilować plik jako C++C lub, odpowiednio. Te opcje mogą spowodować nieoczekiwane nazwy konsolidatora.

W przypadku prototypów funkcji, które mają niezgodne parametry, może być również przyczyną tego błędu. Dekoracja nazwy obejmuje parametry funkcji w końcowej nazwie funkcji dekoracyjnej. Wywołanie funkcji z typami parametrów, które nie pasują do tych w deklaracji funkcji, może również spowodować LNK2001.

Obecnie nie ma żadnych standardów C++ nazewnictwa między dostawcami kompilatora, a nawet między różnymi wersjami kompilatora. Łączenie plików obiektów skompilowanych przez inne kompilatory może nie dawać tego samego schematu nazewnictwa i może powodować nierozpoznane zewnętrzne.

## <a name="see-also"></a>Zobacz też

[Błąd narzędzi konsolidatora LNK2001](../../error-messages/tool-errors/linker-tools-error-lnk2001.md)
