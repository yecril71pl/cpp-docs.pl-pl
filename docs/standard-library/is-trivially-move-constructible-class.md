---
title: Klasa is_trivially_move_constructible | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: type_traits/std::is_trivially_move_constructible
dev_langs: C++
helpviewer_keywords: is_trivially_move_constructible
ms.assetid: 740bdec7-65e5-47b3-b94f-a2479ceac3ec
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: ba32f03d08032bc47373d2389831e52913298d49
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="istriviallymoveconstructible-class"></a>is_trivially_move_constructible — klasa
Testy, jeśli typ ma trivial przenoszenie konstruktora.  
  
## <a name="syntax"></a>Składnia  
  
```
template <class Ty>
struct is_trivially_move_constructible;
```  
  
#### <a name="parameters"></a>Parametry  
 `Ty`  
 Typ do zapytania.  
  
## <a name="remarks"></a>Uwagi  
 Wystąpienie typu predykatu posiada wartość true Jeśli typ `Ty` jest klasa, która ma Konstruktor przenoszący trivial w inny sposób przechowuje wartość false.  
  
 Przenoszenie konstruktora dla klasy `Ty` jest prosta jeśli:  
  
 został niejawnie zadeklarowany.  
  
 jego typy parametrów są odpowiadające niejawne deklaracji  
  
 Klasa `Ty` ma żadnych funkcji wirtualnych  
  
 Klasa `Ty` ma nie wirtualnych typów podstawowych  
  
 Klasa nie ma żadnych członków danych niestatycznych nietrwałe  
  
 wszystkie bezpośrednio podstawowych klasy `Ty` mieć konstruktorów przenoszenia prosta  
  
 klasy wszystkich członków danych niestatycznych typu klasy mają konstruktorów przenoszenia prosta  
  
 klasy wszystkich członków danych niestatycznych tablicy typu klasy mają konstruktorów przenoszenia prosta  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<type_traits >  
  
 **Namespace:** Standard  
  
## <a name="see-also"></a>Zobacz też  
 [< type_traits >](../standard-library/type-traits.md)



