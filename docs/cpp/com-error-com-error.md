---
title: _com_error::_com_error
ms.date: 11/04/2016
f1_keywords:
- _com_error::_com_error
helpviewer_keywords:
- _com_error method [C++]
ms.assetid: 0a69e46c-caab-49ef-b091-eee401253ce6
ms.openlocfilehash: 4ac902f0fda90f77526ef53139ef0d523d8c22e7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180787"
---
# <a name="_com_error_com_error"></a>_com_error::_com_error

**Specyficzne dla firmy Microsoft**

Konstruuje obiekt **_com_error** .

## <a name="syntax"></a>Składnia

```
_com_error(
   HRESULT hr,
   IErrorInfo* perrinfo = NULL,
   bool fAddRef=false) throw( );

_com_error( const _com_error& that ) throw( );
```

#### <a name="parameters"></a>Parametry

*wysoki*<br/>
Informacje o HRESULT.

*perrinfo*<br/>
`IErrorInfo` obiektu.

*fAddRef*<br/>
Wartość domyślna powoduje, że Konstruktor wywołuje AddRef na interfejsie `IErrorInfo` innym niż null. Zapewnia to poprawne zliczanie odwołań w typowym przypadku, gdy własność interfejsu jest przenoszona do obiektu **_com_error** , na przykład:

```cpp
throw _com_error(hr, perrinfo);
```

Jeśli nie chcesz, aby kod przeniesieł własność do obiektu **_com_error** , a `AddRef` jest wymagany do przesunięcia `Release` w destruktorze **_com_error** , Konstruuj obiekt w następujący sposób:

```cpp
_com_error err(hr, perrinfo, true);
```

*przez*<br/>
Istniejący obiekt **_com_error** .

## <a name="remarks"></a>Uwagi

Pierwszy Konstruktor tworzy nowy obiekt z uwzględnieniem elementu HRESULT i opcjonalnego obiektu `IErrorInfo`. Druga tworzy kopię istniejącego obiektu **_com_error** .

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz też

[_com_error, klasa](../cpp/com-error-class.md)
