---
title: setlocale
ms.date: 11/04/2016
f1_keywords:
- setlocale_CPP
- vc-pragma.setlocale
helpviewer_keywords:
- pragmas, setlocale
- setlocale pragma
ms.assetid: e60b43d9-fbdf-4c4e-ac85-805523a13b86
ms.openlocfilehash: b2f28a14b4d4585575a39dd9a936a56a84eeddc4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62179623"
---
# <a name="setlocale"></a>setlocale

Określa ustawienia regionalne (Kraj/Region i język), który będzie używany podczas tłumaczenia Literały ciągu i stałych znaków dwubajtowych.

## <a name="syntax"></a>Składnia

```
#pragma setlocale( "[locale-string]" )
```

## <a name="remarks"></a>Uwagi

Ponieważ algorytm konwersji na znaki wielobajtowe do znaków dwubajtowych mogą się znacząco różnić ustawień regionalnych lub kompilacja może mieć miejsce w innych ustawień regionalnych, z którym będzie uruchamiany plik wykonywalny, ta pragma zapewnia sposób określania docelowych ustawień regionalnych w czasie kompilacji. Gwarantuje to, że ciągi znaków dwubajtowych będą przechowywane w poprawnym formacie.

Wartość domyślna *ciągu ustawień regionalnych* jest "".

The "C" locale maps each character in the string to its value as a **wchar_t** (unsigned short). Inne wartości, które są prawidłowe dla `setlocale` tych wpisów, które znajdują się w [Language Strings](../c-runtime-library/language-strings.md) listy. Na przykład, możesz wydać:

```cpp
#pragma setlocale("dutch")
```

Zdolność do wystawiania ciąg języka zależy od strony kodowej i język obsługi identyfikatorów na tym komputerze.

## <a name="see-also"></a>Zobacz także

[Dyrektywy pragma i słowo kluczowe __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)