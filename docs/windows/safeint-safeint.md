---
title: SafeInt::SafeInt | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SafeInt::SafeInt
- SafeInt
- SafeInt.SafeInt
dev_langs: C++
helpviewer_keywords: SafeInt class, constructor
ms.assetid: 39e6f632-a396-40e6-9ece-cc3d4c5a78ef
caps.latest.revision: "7"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.openlocfilehash: 77ff8395aee764c67a3f90b69f33f4299de4f550
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="safeintsafeint"></a>SafeInt::SafeInt
Konstruuje `SafeInt` obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```  
SafeInt() throw  
  
SafeInt (  
   const T& i  
) throw ()  
  
SafeInt (  
   bool b  
) throw ()  
  
template <typename U>  
SafeInt (  
   const SafeInt <U, E>& u  
)  
  
I template <typename U>  
SafeInt (  
   const U& i  
)  
```  
  
#### <a name="parameters"></a>Parametry  
 [in]`i`  
 Wartość dla nowej `SafeInt` obiektu. Musi to być parametr typu T lub U, w zależności od tego konstruktora.  
  
 [in]`b`  
 Wartość logiczna dla nowej `SafeInt` obiektu.  
  
 [in]`u`  
 A `SafeInt` z typu U. Nowy `SafeInt` obiekt będzie mieć taką samą wartość jak `u`, ale będzie typu T.  
  
 U  
 Typ danych przechowywanych w `SafeInt`. Może to być typu Boolean, znak lub liczbą całkowitą. Jeśli jest typu Liczba całkowita, może być podpisu lub bez znaku i należeć do zakresu od 8 do 64 bitów.  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji o typach szablonu `T` i `E`, zobacz [safeint — klasa](../windows/safeint-class.md).  
  
 Parametr wejściowy dla konstruktora, `i` lub `u`, musi być typu Boolean, znak lub liczbą całkowitą. Jeśli jest innego typu parametru `SafeInt` klasy wywołania [static_assert](../cpp/static-assert.md) wskazująca nieprawidłowy parametr wejściowy.  
  
 Konstruktory, które używają typu szablonu `U` automatycznie przekonwertować na typ określony przez parametr wejściowy `T`. `SafeInt` Klasy konwertuje dane bez utraty danych. Przekazuje do programu obsługi błędów `E` , jeśli nie można przekonwertować danych na typ `T` bez utraty danych.  
  
 Jeśli tworzysz `SafeInt` z parametrem logicznym należy zainicjować wartość natychmiast. Nie można skonstruować `SafeInt` przy użyciu kodu `SafeInt<bool> sb;`. Zostanie wygenerowany błąd kompilacji.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** safeint.h  
  
 **Namespace:** msl::utilities  
  
## <a name="see-also"></a>Zobacz też  
 [Biblioteka SafeInt](../windows/safeint-library.md)   
 [Safeint — klasa](../windows/safeint-class.md)   
 [Safeintexception — klasa](../windows/safeintexception-class.md)