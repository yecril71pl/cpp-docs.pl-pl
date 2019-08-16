---
title: usesgetlasterror (C++ atrybut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.usesgetlasterror
helpviewer_keywords:
- usesgetlasterror attribute
ms.assetid: d149e33d-35a7-46cb-9137-ae6883d86122
ms.openlocfilehash: b14316bd929f4b41b13a76c41e94b31b7534e9d8
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69513895"
---
# <a name="usesgetlasterror"></a>usesgetlasterror

Informuje obiekt wywołujący, że jeśli wystąpi błąd podczas wywoływania tej funkcji, wywołujący może następnie wywołać `GetLastError` , aby pobrać kod błędu.

## <a name="syntax"></a>Składnia

```cpp
[usesgetlasterror]
```

## <a name="remarks"></a>Uwagi

Atrybut **usesgetlasterror** C++ ma takie same funkcje jak atrybut [usesgetlasterror](/windows/win32/Midl/usesgetlasterror) MIDL.

## <a name="example"></a>Przykład

Zobacz przykład [idl_module](idl-module.md) , aby uzyskać przykład korzystania z **usesgetlasterror**.

## <a name="requirements"></a>Wymagania

### <a name="attribute-context"></a>Kontekst atrybutu

|||
|-|-|
|**Dotyczy**|atrybut **modułu**|
|**Powtarzalne**|Nie|
|**Wymagane atrybuty**|Brak|
|**Nieprawidłowe atrybuty**|Brak|

Aby uzyskać więcej informacji na temat kontekstów atrybutów, zobacz [konteksty atrybutów](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz także

[Atrybuty IDL](idl-attributes.md)