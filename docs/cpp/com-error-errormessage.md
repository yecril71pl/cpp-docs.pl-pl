---
title: _com_error::ErrorMessage | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_error::ErrorMessage
dev_langs:
- C++
helpviewer_keywords:
- ErrorMessage method [C++]
ms.assetid: e47335b6-01af-4975-a841-121597479eb7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b8dda27c3f1c535f60856bd9d4a3abb9a51a1a32
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43219923"
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