---
title: _com_error::_com_error
ms.date: 11/04/2016
f1_keywords:
- _com_error::_com_error
helpviewer_keywords:
- _com_error method [C++]
ms.assetid: 0a69e46c-caab-49ef-b091-eee401253ce6
ms.openlocfilehash: 8856289605cce430fdab36d6e3e8b743190e02ea
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62155127"
---
# <a name="comerrorcomerror"></a>_com_error::_com_error

**Microsoft Specific**

Konstruuje **_com_error** obiektu.

## <a name="syntax"></a>Składnia

```
_com_error(
   HRESULT hr,
   IErrorInfo* perrinfo = NULL,
   bool fAddRef=false) throw( );

_com_error( const _com_error& that ) throw( );
```

#### <a name="parameters"></a>Parametry

*godz.*<br/>
Informacje o HRESULT.

*perrinfo*<br/>
`IErrorInfo` obiekt.

*fAddRef*<br/>
Domyślnie powoduje, że Konstruktor może wywołać inną niż null AddRef `IErrorInfo` interfejsu. Zapewnia to poprawne zliczanie w przypadku typowych, której własność interfejsu jest przekazywana do **_com_error** obiektów, takich jak:

```cpp
throw _com_error(hr, perrinfo);
```

Jeśli nie chcesz swój kod, aby przenieść własność na **_com_error** obiektu i `AddRef` jest wymagany, o które zostanie przesunięte `Release` w **_com_error** destruktora, konstruowania obiektu jako następujące:

```cpp
_com_error err(hr, perrinfo, true);
```

*który*<br/>
Istniejące **_com_error** obiektu.

## <a name="remarks"></a>Uwagi

Pierwszy Konstruktor tworzy nowy obiekt, biorąc pod uwagę na HRESULT i opcjonalnie `IErrorInfo` obiektu. Drugi tworzy kopię istniejącego **_com_error** obiektu.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[_com_error, klasa](../cpp/com-error-class.md)