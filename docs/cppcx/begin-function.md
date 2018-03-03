---
title: Rozpocznij funkcja | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/22/2017
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- collection/Windows::Foundation::Collections::begin
dev_langs:
- C++
helpviewer_keywords:
- begin Function
ms.assetid: 5a44fb33-e247-49fd-b7a1-4a5b42e9e1e4
caps.latest.revision: 
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d47244e6428979f5319c9ee02f252ef3e559f7ad
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="begin-function"></a>BEGIN — funkcja
Zwraca wartość wskazującą na początku kolekcji, który jest dostępny za pomocą parametru określonego interfejsu iteratora.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
template <typename T>   
    ::Platform::Collections::VectorIterator<T>   
    begin(  
          IVector<T>^ v         );  
  
template <typename T>   
    ::Platform::Collections::VectorViewIterator<T>   
    begin(  
          IVectorView<T>^ v  
         );   
  
template <typename T>   
    ::Platform::Collections::InputIterator<T>   
    begin(  
          IIterable<T>^ i         );  
  
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Parametr typu szablonu.  
  
 `v`  
 Kolekcja wektor\<T > lub VectorView\<T > obiekty, które są używane przez IVector\<T > lub IVectorView\<T > interfejsu.  
  
 `i`  
 Kolekcja dowolnego obiektów środowiska wykonawczego systemu Windows, które są używane przez IIterable\<T > interfejsu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Iterator, który wskazuje na początku kolekcji.  
  
### <a name="remarks"></a>Uwagi  
 Pierwszy funkcje dwóch szablonów Zwróć Iteratory, a trzeci funkcji szablonu zwracającą iterator wejściowego.  
  
 VectorIterator rozpocząć obiektu, który jest zwracany przez jest iteratora serwera proxy, który przechowuje elementy typu VectorProxy\<T >. Jednak obiekt serwera proxy prawie nigdy nie jest widoczny dla kodu użytkownika. Aby uzyskać więcej informacji, zobacz [kolekcji (C + +/ CX)](../cppcx/collections-c-cx.md).  
  
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** collection.h  
  
 **Namespace:** Windows::Foundation::Collections  
  
## <a name="see-also"></a>Zobacz też  
 [Namespace Windows::Foundation::Collections](../cppcx/windows-foundation-collections-namespace-c-cx.md)