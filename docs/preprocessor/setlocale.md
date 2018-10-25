---
title: setLocale | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- setlocale_CPP
- vc-pragma.setlocale
dev_langs:
- C++
helpviewer_keywords:
- pragmas, setlocale
- setlocale pragma
ms.assetid: e60b43d9-fbdf-4c4e-ac85-805523a13b86
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fa68389b804452e2a17b9880978cd56d291cefb6
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50079418"
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

## <a name="see-also"></a>Zobacz też

[Dyrektywy pragma i słowo kluczowe __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)