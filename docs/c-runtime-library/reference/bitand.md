---
title: bitand
ms.date: 11/04/2016
api_location:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- std::bitand
- std.bitand
- bitand
helpviewer_keywords:
- bitand function
ms.assetid: 279cf9b5-fac1-49de-b329-f1a31b3481fe
ms.openlocfilehash: 771631275ea03cc9d3a6105aa51cd428f1720763
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80171258"
---
# <a name="bitand"></a>bitand

Alternatywa dla operatora &.

## <a name="syntax"></a>Składnia

```C

#define bitand &
```

## <a name="remarks"></a>Uwagi

Makro daje operator

## <a name="example"></a>Przykład

```cpp
// iso646_bitand.cpp
// compile with: /EHsc
#include <iostream>
#include <iso646.h>

int main( )
{
   using namespace std;
   int a = 1, b = 2, result;

   result = a & b;
   cout << result << endl;

   result= a bitand b;
   cout << result << endl;
}
```

```Output
0
0
```

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<iso646. h >
