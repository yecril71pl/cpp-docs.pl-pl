---
title: _com_error::_com_error | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_error::_com_error
dev_langs:
- C++
helpviewer_keywords:
- _com_error method [C++]
ms.assetid: 0a69e46c-caab-49ef-b091-eee401253ce6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 89377e33e56b0796fc850c050c8e79eac86ee07d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46040469"
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