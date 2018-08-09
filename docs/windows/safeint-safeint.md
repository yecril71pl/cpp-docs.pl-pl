---
title: SafeInt::SafeInt | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- SafeInt::SafeInt
- SafeInt
- SafeInt.SafeInt
dev_langs:
- C++
helpviewer_keywords:
- SafeInt class, constructor
ms.assetid: 39e6f632-a396-40e6-9ece-cc3d4c5a78ef
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8cfc0085164cfc9d5f3c8691fb50e0b98f796b32
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2018
ms.locfileid: "40015069"
---
# <a name="safeintsafeint"></a>SafeInt::SafeInt
Konstruuje **SafeInt** obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
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
  
### <a name="parameters"></a>Parametry  
 [in] *i*  
 Wartość dla nowej klasy **SafeInt** obiektu. Musi to być parametrem typu T lub U, w zależności od tego konstruktora.  
  
 [in] *b*  
 Wartość logiczna dla nowej **SafeInt** obiektu.  
  
 [in] *u*  
 A **SafeInt** z typu U. Nowy **SafeInt** obiekt będzie miał taką samą wartość jak *u*, ale będą typu T.  
  
 U  
 Typ danych przechowywanych w **SafeInt**. Może to być atrybut typu wartość logiczna, znaku lub liczba całkowita typu. Jeśli typ liczby całkowitej, mogą być podpisane lub niepodpisane i mieć długość od 8 do 64 bitów.  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji na temat typów szablonu `T` i `E`, zobacz [safeint — klasa](../windows/safeint-class.md).  
  
 Parametr wejściowy dla konstruktora, *i* lub *u*, musi być typu wartość logiczna, znaku lub liczba całkowita. Jeśli jest innego typu parametru **SafeInt** klasy wywołania [static_assert](../cpp/static-assert.md) do wskazania nieprawidłowy parametr wejściowy.  
  
 Konstruktory, które używają typu szablonu `U` automatycznie przekonwertować parametru wejściowego typu określonego przez `T`. **SafeInt** klasy konwertuje dane bez utraty danych. Wysyła raporty do programu obsługi błędów `E` gdy go nie może przekonwertować danych na typ `T` bez utraty danych.  
  
 Jeśli tworzysz **SafeInt** z parametrem logicznym należy zainicjować wartości natychmiast. Nie można skonstruować **SafeInt** przy użyciu kodu `SafeInt<bool> sb;`. Spowoduje to wygenerowanie błędu kompilacji.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** safeint.h  
  
 **Namespace:** msl::utilities  
  
## <a name="see-also"></a>Zobacz też  
 [Biblioteka SafeInt](../windows/safeint-library.md)   
 [Safeint — klasa](../windows/safeint-class.md)   
 [SafeIntException, klasa](../windows/safeintexception-class.md)