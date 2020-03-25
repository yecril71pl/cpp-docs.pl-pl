---
title: _com_error::ErrorMessage
ms.date: 11/04/2016
f1_keywords:
- _com_error::ErrorMessage
helpviewer_keywords:
- ErrorMessage method [C++]
ms.assetid: e47335b6-01af-4975-a841-121597479eb7
ms.openlocfilehash: b5e884956b5a51d3c714f1a81dc6945409f74f4b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180670"
---
# <a name="_com_errorerrormessage"></a>_com_error::ErrorMessage

**Specyficzne dla firmy Microsoft**

Pobiera komunikat ciągu dla HRESULT przechowywanego w obiekcie `_com_error`.

## <a name="syntax"></a>Składnia

```
const TCHAR * ErrorMessage( ) const throw( );
```

## <a name="return-value"></a>Wartość zwracana

Zwraca komunikat ciągu dla HRESULT zarejestrowanego w obiekcie `_com_error`. Jeśli HRESULT jest mapowanym 16-bitowym [kodostrzeżenia](../cpp/com-error-wcode.md), zwracany jest komunikat ogólny "`IDispatch error #<wCode>`". Jeśli wiadomość nie zostanie znaleziona, zostanie zwrócony komunikat generyczny "`Unknown error #<hresult>`". Zwrócony ciąg jest ciągiem Unicode lub wielobajtowym, w zależności od stanu makra _UNICODE.

## <a name="remarks"></a>Uwagi

Pobiera odpowiedni tekst komunikatu systemu dla HRESULT zarejestrowanego w obiekcie `_com_error`. Tekst komunikatu systemowego jest uzyskiwany przez wywołanie funkcji Win32 [FormatMessage](/windows/win32/api/winbase/nf-winbase-formatmessage) . Zwracany ciąg jest przypisywany przez interfejs API `FormatMessage` i jest wydawany, gdy obiekt `_com_error` zostanie zniszczony.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz też

[_com_error, klasa](../cpp/com-error-class.md)
