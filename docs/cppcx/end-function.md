---
title: End Function | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/22/2017
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: collection/Windows::Foundation::Collections::end
dev_langs: C++
helpviewer_keywords: end Function
ms.assetid: fb837bff-fc76-4bae-9096-facf0e03041c
caps.latest.revision: "4"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.openlocfilehash: f4030728c296a6dd234b6ad181d83ef072b06dd9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="end-function"></a>End — funkcja
Zwraca wartość wskazującą za końcem kolekcji, który jest dostępny za pomocą parametru określonego interfejsu iteratora.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
template <typename T>  
    ::Platform::Collections::VectorIterator<T>   
    end(  
        IVector<T>^ v       );  
  
template <typename T>  
    ::Platform::Collections::VectorViewIterator<T>   
    end(  
        IVectorView<T>^ v  
       );  
template <typename T>   
    ::Platform::Collections::InputIterator<T>   
    end(  
        IIterable<T>^ i  
       );  
  
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Parametr typu szablonu.  
  
 `v`  
 Kolekcja wektor\<T > lub VectorView\<T > obiekty, które są używane przez IVector\<T >, lub IVectorView\<T > interfejsu.  
  
 `i`  
 Kolekcja arbitraty środowiska wykonawczego systemu Windows obiekty, które są używane przez IIterable\<T > interfejsu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Iteratora wskazujący za końcem kolekcji.  
  
### <a name="remarks"></a>Uwagi  
 Pierwszy funkcje dwóch szablonów Zwróć Iteratory, a trzeci funkcji szablonu zwracającą iterator wejściowego.  
  
 [Platform::Collections::VectorViewIterator](../cppcx/platform-collections-vectorviewiterator-class.md) obiektu, który jest zwracany przez `end` jest iteratora serwera proxy, który przechowuje elementy typu `VectorProxy<T>`. Jednak obiekt serwera proxy prawie nigdy nie jest widoczny dla kodu użytkownika. Aby uzyskać więcej informacji, zobacz [kolekcji (C + +/ CX)](../cppcx/collections-c-cx.md).  
  
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** collection.h  
  
 **Namespace:** Windows::Foundation::Collections  
  
## <a name="see-also"></a>Zobacz też  
 [Namespace Windows::Foundation::Collections](../cppcx/windows-foundation-collections-namespace-c-cx.md)