---
title: usesgetlasterror — (atrybut C++ COM) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.usesgetlasterror
dev_langs:
- C++
helpviewer_keywords:
- usesgetlasterror attribute
ms.assetid: d149e33d-35a7-46cb-9137-ae6883d86122
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: bb08e2442e34c4d579e568c68d240accdfdbde59
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50074244"
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

## <a name="see-also"></a>Zobacz też

[Atrybuty IDL](idl-attributes.md)