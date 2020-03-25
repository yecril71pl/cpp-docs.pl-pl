---
title: cpp_quote (C++ atrybut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.cpp_quote
helpviewer_keywords:
- cpp_quote attribute
ms.assetid: f75327ff-42bd-498b-9177-7ffa25427e1f
ms.openlocfilehash: 451313b5bd1eb5011f1175de5c3bcfe6fb054299
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214919"
---
# <a name="cpp_quote"></a>cpp_quote

Emituje określony ciąg bez znaków cudzysłowu do wygenerowanego pliku IDL.

## <a name="syntax"></a>Składnia

```cpp
[ cpp_quote("statement") ];
```

### <a name="parameters"></a>Parametry

*Merge*<br/>
Instrukcja języka C.

## <a name="remarks"></a>Uwagi

Atrybut **cpp_quote** C++ jest przydatny, jeśli chcesz umieścić dyrektywę preprocesora w pliku. idl.

Można również użyć **cpp_quote** i wygenerować plik h jako część kompilacji MIDL. Na przykład, jeśli masz plik C++ nagłówka, który używa C++ atrybutów IDL, ale nie można użyć tego pliku do pewnego zadania, można skompilować go w celu utworzenia pliku MIDL. h, który powinien być w stanie używać.

Atrybut **cpp_quote** ma taką samą funkcjonalność jak atrybut [cpp_quote](/windows/win32/Midl/cpp-quote) MIDL.

## <a name="example"></a>Przykład

Zobacz przykład dla [podwójnego](dual.md) przykładu użycia **cpp_quote**.

## <a name="requirements"></a>Wymagania

### <a name="attribute-context"></a>Kontekst atrybutu

|||
|-|-|
|**Dotyczy**|Dowolnym miejscu|
|**Powtarzalne**|Nie|
|**Wymagane atrybuty**|None|
|**Nieprawidłowe atrybuty**|None|

Aby uzyskać więcej informacji na temat kontekstów atrybutów, zobacz [konteksty atrybutów](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz też

[Atrybuty IDL](idl-attributes.md)<br/>
[Oddzielne atrybuty](stand-alone-attributes.md)
