---
title: Makra obsługi wyjątków
ms.date: 11/04/2016
f1_keywords:
- atldef/ATL::_ATLCATCH
- atldef/ATL::_ATLCATCHALL
- atldef/ATL::_ATLTRY
helpviewer_keywords:
- exception handling, macros
- C++ exception handling, macros
ms.assetid: a8385d34-3fb0-4006-a42a-de045cacf0f4
ms.openlocfilehash: 2beffbbed0efee799005190bd7fd071a2087e4d9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330084"
---
# <a name="exception-handling-macros"></a>Makra obsługi wyjątków

Te makra zapewniają obsługę wyjątków.

|||
|-|-|
|[_ATLCATCH](#_atlcatch)|Instrukcji do obsługi błędów występujących w `_ATLTRY`skojarzonym .|
|[_ATLCATCHALL](#_atlcatchall)|Instrukcji do obsługi błędów występujących w `_ATLTRY`skojarzonym .|
|[_ATLTRY](#_atltry)|Oznacza sekcję kodu strzeżonego, w której może wystąpić błąd.|

## <a name="requirements"></a>Wymagania:

**Nagłówek:** atldef.h

## <a name="_atlcatch"></a><a name="_atlcatch"></a>_ATLCATCH

Instrukcji do obsługi błędów występujących w `_ATLTRY`skojarzonym .

```
_ATLCATCH(e)
```

### <a name="parameters"></a>Parametry

*E*<br/>
Wyjątek do połowu.

### <a name="remarks"></a>Uwagi

Używany w `_ATLTRY`połączeniu z . Rozwiązuje [z funkcją catch(CAtlException e)](../../cpp/try-throw-and-catch-statements-cpp.md) dla obsługi danego typu wyjątków języka C++.

## <a name="_atlcatchall"></a><a name="_atlcatchall"></a>_ATLCATCHALL

Instrukcji do obsługi błędów występujących w `_ATLTRY`skojarzonym .

```
_ATLCATCHALL
```

### <a name="remarks"></a>Uwagi

Używany w `_ATLTRY`połączeniu z . Rozwiązuje dla C++ [catch(...)](../../cpp/try-throw-and-catch-statements-cpp.md) do obsługi wszystkich typów wyjątków C++.

## <a name="_atltry"></a><a name="_atltry"></a>_ATLTRY

Oznacza sekcję kodu strzeżonego, w której może wystąpić błąd.

```
_ATLTRY
```

### <a name="remarks"></a>Uwagi

Używany w połączeniu z [_ATLCATCH](#_atlcatch) lub [_ATLCATCHALL](#_atlcatchall). Rozwiązuje [próbę](../../cpp/try-throw-and-catch-statements-cpp.md)symbolu C++ .

## <a name="see-also"></a>Zobacz też

[Makra](../../atl/reference/atl-macros.md)
