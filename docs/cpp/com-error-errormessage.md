---
title: _com_error::ErrorMessage
ms.date: 11/04/2016
f1_keywords:
- _com_error::ErrorMessage
helpviewer_keywords:
- ErrorMessage method [C++]
ms.assetid: e47335b6-01af-4975-a841-121597479eb7
ms.openlocfilehash: b1c1b5a79cdf5ee2a4a17d969d23ce0d0d85ab54
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50504497"
---
# <a name="comerrorerrormessage"></a>_com_error::ErrorMessage

**Microsoft Specific**

Pobiera ciąg komunikatu dla przechowywanych we właściwości HRESULT `_com_error` obiektu.

## <a name="syntax"></a>Składnia

```
const TCHAR * ErrorMessage( ) const throw( );
```

## <a name="return-value"></a>Wartość zwracana

Zwraca ciąg komunikatu dla HRESULT rejestrować się w ramach `_com_error` obiektu. Jeśli HRESULT jest zamapowany 16-bitowych [wcode —](../cpp/com-error-wcode.md), następnie zostanie wyświetlony komunikat ogólny "`IDispatch error #<wCode>`" jest zwracany. Jeśli żaden komunikat nie zostanie znaleziony następnie zostanie wyświetlony komunikat ogólny "`Unknown error #<hresult>`" jest zwracany. Unicode lub wielobajtowego ciągu, w zależności od stanu — makro _UNICODE jest zwracanego ciągu.

## <a name="remarks"></a>Uwagi

Pobiera odpowiedni system tekst komunikatu dla HRESULT rejestrować się w ramach `_com_error` obiektu. Tekst komunikatu systemu są uzyskiwane poprzez wywołanie Win32 [FormatMessage](/windows/desktop/api/winbase/nf-winbase-formatmessage) funkcji. Ciąg zwracany jest przydzielany przez `FormatMessage` interfejsu API, a po wydaniu `_com_error` niszczony jest obiekt.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[_com_error, klasa](../cpp/com-error-class.md)