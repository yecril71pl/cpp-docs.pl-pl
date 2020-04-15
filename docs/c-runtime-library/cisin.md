---
title: _CIsin
ms.date: 4/2/2020
api_name:
- _CIsin
- _o__CIsin
api_location:
- msvcr80.dll
- msvcr100.dll
- msvcrt.dll
- msvcr110.dll
- msvcr120.dll
- msvcr90.dll
- msvcr110_clr0400.dll
- api-ms-win-crt-math-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- CIsin
- _CIsin
helpviewer_keywords:
- _CIsin intrinsic
- CIsin intrinsic
ms.assetid: f215f39a-2341-4f1c-ba8e-cb522451ceb2
ms.openlocfilehash: 8ed8bc0a4b62e3d68ed05a1955b360919838209d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81349539"
---
# <a name="_cisin"></a>_CIsin

Oblicza sinus najwyższej wartości w stosie zmiennoprzecinkowym.

## <a name="syntax"></a>Składnia

```C
void __cdecl _CIsin();
```

## <a name="remarks"></a>Uwagi

Ta wewnętrzna wersja funkcji [grzechu](../c-runtime-library/reference/sin-sinf-sinl.md) ma wyspecjalizowaną konwencję wywoływania, którą kompilator rozumie. Przyspiesza wykonanie, ponieważ zapobiega generowaniu kopii i pomaga w alokacji rejestru.

Wynikowa wartość jest wypychany na górze stosu zmiennoprzecinkowego.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](global-state.md).

## <a name="requirements"></a>Wymagania

**Platforma:** x86

## <a name="see-also"></a>Zobacz też

[Alfabetyczne zestawienie funkcji](../c-runtime-library/reference/crt-alphabetical-function-reference.md)<br/>
[sin, sinf, sinl](../c-runtime-library/reference/sin-sinf-sinl.md)<br/>
