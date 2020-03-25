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
ms.openlocfilehash: b0692c9befaa6b7e787ada624dcbb56b074c9f9d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80160466"
---
# <a name="_variant_tchangetype"></a>_variant_t::ChangeType

**Specyficzne dla firmy Microsoft**

Zmienia typ obiektu `_variant_t` na wskazany `VARTYPE`.

## <a name="syntax"></a>Składnia

```
void ChangeType(
   VARTYPE vartype,
   const _variant_t* pSrc = NULL
);
```

#### <a name="parameters"></a>Parametry

*VARTYPE*<br/>
`VARTYPE` dla tego obiektu `_variant_t`.

*pSrc*<br/>
Wskaźnik do obiektu `_variant_t` do przekonwertowania. Jeśli ta wartość jest RÓWNa NULL, konwersja jest wykonywana na miejscu.

## <a name="remarks"></a>Uwagi

Ta funkcja członkowska Konwertuje obiekt `_variant_t` na wskazany `VARTYPE`. Jeśli *pSrc* ma wartość null, konwersja jest wykonywana, w przeciwnym razie ten obiekt `_variant_t` jest kopiowany z *pSrc* , a następnie konwertowany.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz też

[_variant_t, klasa](../cpp/variant-t-class.md)
