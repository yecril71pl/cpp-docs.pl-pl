---
title: Rozpocznij funkcja | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/22/2017
ms.technology: cpp-windows
ms.topic: language-reference
f1_keywords:
- collection/Windows::Foundation::Collections::begin
dev_langs:
- C++
helpviewer_keywords:
- begin Function
ms.assetid: 5a44fb33-e247-49fd-b7a1-4a5b42e9e1e4
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7c1a8c09e43613014b43ef4e3c075a54cdd90e08
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33086515"
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