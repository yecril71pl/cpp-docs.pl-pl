---
title: _com_error::ErrorMessage | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- _com_error::ErrorMessage
dev_langs:
- C++
helpviewer_keywords:
- ErrorMessage method [C++]
ms.assetid: e47335b6-01af-4975-a841-121597479eb7
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e8690c23acf6e42d355cf122f59f54e19cc36d66
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="comerrorerrormessage"></a>_com_error::ErrorMessage
**Dotyczące firmy Microsoft**  
  
 Pobiera ciąg komunikatu dla `HRESULT` przechowywane w `_com_error` obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
const TCHAR * ErrorMessage( ) const throw( );  
  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca ciąg komunikatu dla `HRESULT` zarejestrowane w ramach `_com_error` obiektu. Jeśli `HRESULT` jest mapowanych 16-bitowy [Kodostrzeżenia](../cpp/com-error-wcode.md), następnie zostanie wyświetlony komunikat ogólny "`IDispatch error #<wCode>`" jest zwracany. Jeśli żaden komunikat nie zostanie znaleziony następnie zostanie wyświetlony komunikat ogólny "`Unknown error #<hresult>`" jest zwracany. Jest zwracany ciąg Unicode lub ciąg wielobajtowy, w zależności od stanu **_unicode —** makra.  
  
## <a name="remarks"></a>Uwagi  
 Pobiera tekst komunikatu odpowiedni system `HRESULT` zarejestrowane w ramach `_com_error` obiektu. Tekst komunikatu systemu są uzyskiwane poprzez wywołanie Win32 [FormatMessage](http://msdn.microsoft.com/library/windows/desktop/ms679351) funkcji. Zwrócony ciąg jest przydzielany przez `FormatMessage` interfejsu API, a po wydaniu `_com_error` obiekt zostanie zniszczony.  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [_com_error, klasa](../cpp/com-error-class.md)