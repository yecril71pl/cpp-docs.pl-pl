---
title: Eksportuj | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.export
dev_langs:
- C++
helpviewer_keywords:
- export attribute
ms.assetid: 70b3e848-fad6-4e09-8c72-be60ca72a4df
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e696b3c141a83882af67e72039c164a0f917d446
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42611203"
---
# <a name="export"></a>export

Powoduje to struktura danych, należy umieścić w pliku .idl.

## <a name="syntax"></a>Składnia

```cpp
[export]
```

## <a name="remarks"></a>Uwagi

**Wyeksportować** C++ atrybutu powoduje, że struktury danych, można umieścić w pliku .idl i następnie być dostępne w bibliotece typów w formacie zgodnym z pliku binarnego, który sprawia, że dostępne w dowolnym języku.

Nie można zastosować **wyeksportować** atrybutów do klasy, nawet wtedy, gdy klasa ma tylko publiczne elementy członkowskie (odpowiednik **struktury**).

Jeśli eksportujesz nienazwane **wyliczenia** lub **struktury**, otrzymuje nazwę, która rozpoczyna się od **__unnamed**<em>x</em>, gdzie *x* jest to numer kolejny.

Definicje typów prawidłowe eksportu są typy podstawowe, struktury, złożenia, wyliczenia lub wpisz identyfikatory.  Zobacz [typedef](http://msdn.microsoft.com/library/windows/desktop/aa367287) Aby uzyskać więcej informacji.

## <a name="example"></a>Przykład

Poniższy kod przedstawia sposób użycia **wyeksportować** atrybutu:

```cpp
// cpp_attr_ref_export.cpp
// compile with: /LD
[module(name="MyLibrary")];

[export]
struct MyStruct {
   int i;
};
```

## <a name="requirements"></a>Wymagania

### <a name="attribute-context"></a>Kontekst atrybutu

|||
|-|-|
|**Dotyczy**|**Unia**, **typedef**, **wyliczenia**, **struktury**, lub **interfejsu**|
|**Powtarzalne**|Nie|
|**Wymaganych atrybutów**|Brak|
|**Nieprawidłowe atrybuty**|Brak|

Aby uzyskać więcej informacji, zobacz [konteksty atrybutu](../windows/attribute-contexts.md).

## <a name="see-also"></a>Zobacz też

[Atrybuty kompilatora](../windows/compiler-attributes.md)  
[Atrybuty Typedef, Enum, Union oraz Struct](../windows/typedef-enum-union-and-struct-attributes.md)  