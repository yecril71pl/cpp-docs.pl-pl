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
ms.openlocfilehash: cf4b7ffb8c6b197dc1c4eea4b6c569e173bb188d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50544407"
---
# <a name="exception-handling-macros"></a>Makra obsługi wyjątków

Te makra obsługi wyjątków.

|||
|-|-|
|[_ATLCATCH](#_atlcatch)|Liczba zapytań: do obsługi błędów występujących w skojarzonym `_ATLTRY`.|
|[_ATLCATCHALL](#_atlcatchall)|Liczba zapytań: do obsługi błędów występujących w skojarzonym `_ATLTRY`.|
|[_ATLTRY](#_atltry)|Oznacza sekcji chronionej kodu, gdzie prawdopodobnie może wystąpić błąd.|

## <a name="requirements"></a>Wymagania:

**Nagłówek:** atldef.h

##  <a name="_atlcatch"></a>  _ATLCATCH

Liczba zapytań: do obsługi błędów występujących w skojarzonym `_ATLTRY`.

```
_ATLCATCH(e)
```

### <a name="parameters"></a>Parametry

*e*<br/>
Wyjątek do przechwytywania.

### <a name="remarks"></a>Uwagi

Używany w połączeniu z `_ATLTRY`. Jest rozpoznawana jako C++ [catch (CAtlException e)](../../cpp/try-throw-and-catch-statements-cpp.md) do obsługi danego typu wyjątki C++.

##  <a name="_atlcatchall"></a>  _ATLCATCHALL

Liczba zapytań: do obsługi błędów występujących w skojarzonym `_ATLTRY`.

```
_ATLCATCHALL
```

### <a name="remarks"></a>Uwagi

Używany w połączeniu z `_ATLTRY`. C++ jest rozpoznawana jako [catch(...) ](../../cpp/try-throw-and-catch-statements-cpp.md) do obsługi wszystkich typów wyjątków języka C++.

##  <a name="_atltry"></a>  _ATLTRY

Oznacza sekcji chronionej kodu, gdzie prawdopodobnie może wystąpić błąd.

```
_ATLTRY
```

### <a name="remarks"></a>Uwagi

Używany w połączeniu z [_ATLCATCH](#_atlcatch) lub [_ATLCATCHALL](#_atlcatchall). Jest rozpoznawana jako C++ symbol [spróbuj](../../cpp/try-throw-and-catch-statements-cpp.md).

## <a name="see-also"></a>Zobacz też

[Makra](../../atl/reference/atl-macros.md)
