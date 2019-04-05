---
title: cpp_quote — (atrybut COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.cpp_quote
helpviewer_keywords:
- cpp_quote attribute
ms.assetid: f75327ff-42bd-498b-9177-7ffa25427e1f
ms.openlocfilehash: 378435ced5a541785b7b32bc9d2f408034d5a2d8
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "59024688"
---
# <a name="cppquote"></a>cpp_quote

Generuje określony ciąg bez znaków cudzysłowu do pliku .idl wygenerowany.

## <a name="syntax"></a>Składnia

```cpp
[ cpp_quote("statement") ];
```

### <a name="parameters"></a>Parametry

*Instrukcja*<br/>
Instrukcja języka C.

## <a name="remarks"></a>Uwagi

**Cpp_quote —** C++ atrybut jest przydatna, jeśli chcesz umieścić dyrektywy preprocesora w pliku .idl.

Można również użyć **cpp_quote —** i Wygeneruj plik .h jako część kompilacji MIDL. Na przykład jeśli masz plik nagłówka C++, który używa atrybuty C++ IDL, ale nie można użyć tego pliku dla niektórych zadań, następnie będzie można kompilować go, aby utworzyć plik MIDL generowane .h, powinno być możliwe do użycia.

**Cpp_quote —** atrybut ma taką samą funkcjonalność jak [cpp_quote —](/windows/desktop/Midl/cpp-quote) atrybutów w MIDL.

## <a name="example"></a>Przykład

Zobacz przykład [podwójną](dual.md) na przykład użyć sposób używania **cpp_quote —**.

## <a name="requirements"></a>Wymagania

### <a name="attribute-context"></a>Kontekst atrybutu

|||
|-|-|
|**Informacje zawarte w tym artykule dotyczą**|Dowolne miejsce|
|**Powtarzalne**|Nie|
|**Wymaganych atrybutów**|Brak|
|**Nieprawidłowe atrybuty**|Brak|

Aby uzyskać więcej informacji na temat konteksty atrybutu zobacz [konteksty atrybutu](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz także

[atrybuty IDL](idl-attributes.md)<br/>
[Oddzielne atrybuty](stand-alone-attributes.md)