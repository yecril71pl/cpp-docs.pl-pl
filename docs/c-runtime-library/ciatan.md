---
title: _CIatan
ms.date: 4/2/2020
api_name:
- _CIatan
- _o__CIatan
api_location:
- msvcr120.dll
- msvcr110.dll
- msvcrt.dll
- msvcr80.dll
- msvcr100.dll
- msvcr90.dll
- msvcr110_clr0400.dll
- api-ms-win-crt-math-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _CIatan
- CIatan
helpviewer_keywords:
- CIatan intrinsic
- _CIatan intrinsic
ms.assetid: 3baa0429-fe46-4bab-8b00-868e2186dc8c
ms.openlocfilehash: 5a501d8cf6d2e1dba87239337049d7e5ee0b953d
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81745843"
---
# <a name="_ciatan"></a>_CIatan

Oblicza arctangent najwyższej wartości na stosie.

## <a name="syntax"></a>Składnia

```cpp
void __cdecl _CIatan();
```

## <a name="remarks"></a>Uwagi

Ta wersja `atan` funkcji ma wyspecjalizowaną konwencję wywoływania, którą kompilator rozumie. Przyspiesza wykonanie, ponieważ zapobiega generowaniu kopii i pomaga w alokacji rejestru.

Wynikowa wartość jest wypychany na górze stosu.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](global-state.md).

## <a name="requirements"></a>Wymagania

**Platforma:** x86

## <a name="see-also"></a>Zobacz też

[Alfabetyczne zestawienie funkcji](../c-runtime-library/reference/crt-alphabetical-function-reference.md)<br/>
[atan, atanf, atanl, atan2, atan2f, atan2l](../c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l.md)
