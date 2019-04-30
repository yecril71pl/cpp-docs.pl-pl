---
title: usesgetlasterror — (atrybut COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.usesgetlasterror
helpviewer_keywords:
- usesgetlasterror attribute
ms.assetid: d149e33d-35a7-46cb-9137-ae6883d86122
ms.openlocfilehash: 9f050bbf69edf1ab8327a283299cb5e687ce5380
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62407071"
---
# <a name="usesgetlasterror"></a>usesgetlasterror

Informuje obiekt wywołujący, że jeśli występuje błąd podczas wywoływania tej funkcji, następnie element wywołujący może wywoływać `GetLastError` można pobrać kod błędu.

## <a name="syntax"></a>Składnia

```cpp
[usesgetlasterror]
```

## <a name="remarks"></a>Uwagi

**Usesgetlasterror —** atrybut C++ ma taką samą funkcjonalność jak [usesgetlasterror —](/windows/desktop/Midl/usesgetlasterror) atrybutów w MIDL.

## <a name="example"></a>Przykład

Zobacz [idl_module](idl-module.md) przykład przykład sposobu użycia **usesgetlasterror —**.

## <a name="requirements"></a>Wymagania

### <a name="attribute-context"></a>Kontekst atrybutu

|||
|-|-|
|**Dotyczy**|**Moduł** atrybutu|
|**Powtarzalne**|Nie|
|**Wymaganych atrybutów**|Brak|
|**Nieprawidłowe atrybuty**|Brak|

Aby uzyskać więcej informacji na temat konteksty atrybutu zobacz [konteksty atrybutu](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz także

[Atrybuty IDL](idl-attributes.md)