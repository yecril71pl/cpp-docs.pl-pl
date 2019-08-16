---
title: _com_error::ErrorMessage
ms.date: 11/04/2016
f1_keywords:
- _com_error::ErrorMessage
helpviewer_keywords:
- ErrorMessage method [C++]
ms.assetid: e47335b6-01af-4975-a841-121597479eb7
ms.openlocfilehash: 44fc9755cd69050ea82145636f01614258943794
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69500578"
---
# <a name="_com_errorerrormessage"></a>_com_error::ErrorMessage

**Microsoft Specific**

Pobiera komunikat ciągu dla HRESULT przechowywanego w `_com_error` obiekcie.

## <a name="syntax"></a>Składnia

```
const TCHAR * ErrorMessage( ) const throw( );
```

## <a name="return-value"></a>Wartość zwracana

Zwraca komunikat ciągu dla HRESULT zarejestrowanego w `_com_error` obiekcie. Jeśli HRESULT jest mapowanym 16-bitowym [kodostrzeżenia](../cpp/com-error-wcode.md), zwracany jest komunikat generyczny`IDispatch error #<wCode>`"". Jeśli wiadomość nie zostanie znaleziona, zostanie zwrócony komunikat generyczny "`Unknown error #<hresult>`". Zwrócony ciąg jest ciągiem Unicode lub wielobajtowym, w zależności od stanu makra _UNICODE.

## <a name="remarks"></a>Uwagi

Pobiera odpowiedni tekst komunikatu systemowego dla HRESULT zarejestrowanego `_com_error` w obiekcie. Tekst komunikatu systemowego jest uzyskiwany przez wywołanie funkcji Win32 [FormatMessage](/windows/win32/api/winbase/nf-winbase-formatmessage) . Zwracany ciąg jest przypisywany przez `FormatMessage` interfejs API i jest wydawany, `_com_error` gdy obiekt zostanie zniszczony.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[_com_error, klasa](../cpp/com-error-class.md)