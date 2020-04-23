---
title: _variant_t::ChangeType
ms.date: 11/04/2016
f1_keywords:
- _variant_t::ChangeType
- _variant_t.ChangeType
helpviewer_keywords:
- ChangeType method [C++]
- VARIANT object [C++], ChangeType
- VARIANT object
ms.assetid: 829d2eeb-3338-4a88-9dce-0ca145f47aac
ms.openlocfilehash: c2283158856a6781ab2e12c51f4e2ad0e4f1d531
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81750731"
---
# <a name="_variant_tchangetype"></a>_variant_t::ChangeType

**Specyficzne dla firmy Microsoft**

Zmienia typ obiektu `_variant_t` na wskazany `VARTYPE`.

## <a name="syntax"></a>Składnia

```cpp
void ChangeType(
   VARTYPE vartype,
   const _variant_t* pSrc = NULL
);
```

#### <a name="parameters"></a>Parametry

*Vartype*<br/>
Dla `VARTYPE` tego `_variant_t` obiektu.

*Psrc*<br/>
Wskaźnik do `_variant_t` obiektu, który ma zostać przekonwertowany. Jeśli ta wartość ma wartość NULL, konwersja odbywa się na miejscu.

## <a name="remarks"></a>Uwagi

Ta funkcja elementu `_variant_t` członkowskiego konwertuje `VARTYPE`obiekt na wskazany . Jeśli *pSrc* ma wartość NULL, konwersja `_variant_t` odbywa się na miejscu, w przeciwnym razie ten obiekt jest kopiowany z *pSrc,* a następnie konwertowany.

**ZAKOŃCZ Specyficzne dla firmy Microsoft**

## <a name="see-also"></a>Zobacz też

[Klasa _variant_t](../cpp/variant-t-class.md)
