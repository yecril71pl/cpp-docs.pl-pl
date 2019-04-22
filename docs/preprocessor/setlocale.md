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
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59022428"
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

Ustawień regionalnych "C" mapuje każdy znak w ciągu na wartość jako **wchar_t** (typ unsigned short). Inne wartości, które są prawidłowe dla `setlocale` tych wpisów, które znajdują się w [Language Strings](../c-runtime-library/language-strings.md) listy. Na przykład, możesz wydać:

```cpp
#pragma setlocale("dutch")
```

Zdolność do wystawiania ciąg języka zależy od strony kodowej i język obsługi identyfikatorów na tym komputerze.

## <a name="see-also"></a>Zobacz także

[Dyrektywy pragma i słowo kluczowe __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)