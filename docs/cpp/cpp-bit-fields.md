---
title: "Pola bitowe języka C++ | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- bitfields [C++]
- fields [C++], bit
- bit fields
ms.assetid: 6f4b62e3-cc1d-4e5d-bf34-05904104f71a
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 01a346054fff0f8f3a9a1407c17e28e8dc234a57
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="c-bit-fields"></a>Pola bitowe języka C++
Klasy i struktury może zawierać elementów członkowskich, które zajmują mniej miejsca niż typ całkowity. Elementy te są określone jako pól bitowych. Składnia pola bitowego *deklarator elementu członkowskiego* specyfikacji w następujący sposób:  
  
## <a name="syntax"></a>Składnia  
  
```  
  
declarator  : constant-expression  
```  
  
## <a name="remarks"></a>Uwagi  
 (Opcjonalnie) `declarator` jest nazwą, za pomocą którego element członkowski jest dostępny w programie. Musi ona typ całkowity (w tym typy wyliczane). *Wyrażenia* określa liczbę bitów zajmuje element członkowski w strukturze. Pola bitowe anonimowy — to znaczy pola bitowego członków z nie identyfikatora — może służyć do uzupełnienia.  
  
> [!NOTE]
>  Pole bitowe nienazwane szerokości 0 wymusza wyrównanie dalej pola bitowego do następnego `type` granic, gdzie `type` jest typem elementu członkowskiego.  
  
 Poniższy przykład deklaruje struktury, która zawiera pola bitowe:  
  
```  
// bit_fields1.cpp  
// compile with: /LD  
struct Date {  
   unsigned short nWeekDay  : 3;    // 0..7   (3 bits)  
   unsigned short nMonthDay : 6;    // 0..31  (6 bits)  
   unsigned short nMonth    : 5;    // 0..12  (5 bits)  
   unsigned short nYear     : 8;    // 0..100 (8 bits)  
};  
```  
  
 Układ pamięci koncepcyjnym typu obiektu `Date` przedstawiono na poniższej ilustracji.  
  
 ![Układ pamięci obiektu data](../cpp/media/vc38uq1.png "vc38UQ1")  
Układ pamięci Date — obiekt  
  
 Należy pamiętać, że `nYear` jest 8 bitów i spowodowałoby przepełnienie granic programu word z zadeklarowanym typem **niepodpisane krótko**. W związku z tym rozpoczyna się na początku nowego **niepodpisane krótko**. Nie jest konieczne, wszystkie-bitowy pola mieści się w jeden obiekt typu źródłowego; nowe jednostki magazynu są przydzielane zgodnie z liczbą bitów w deklaracji.  
  
 **Dotyczące firmy Microsoft**  
  
 Porządkowanie danych zadeklarowany jako pola bitowego jest z bitowego niskiego na wysoki, jak pokazano na rysunku powyżej.  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
 Jeśli w deklaracji struktury zawiera nienazwane pole długość wynosi 0, jak pokazano w poniższym przykładzie  
  
```  
// bit_fields2.cpp  
// compile with: /LD  
struct Date {  
   unsigned nWeekDay  : 3;    // 0..7   (3 bits)  
   unsigned nMonthDay : 6;    // 0..31  (6 bits)  
   unsigned           : 0;    // Force alignment to next boundary.  
   unsigned nMonth    : 5;    // 0..12  (5 bits)  
   unsigned nYear     : 8;    // 0..100 (8 bits)  
};  
```  
  
 Układ pamięci jest, jak pokazano na poniższej ilustracji.  
  
 ![Układ obiektu Data zero &#45; długość pola bitowego](../cpp/media/vc38uq2.png "vc38UQ2")  
Układ obiekt Date pole bitowe o zerowej długości  
  
 Podstawowy typ pola bitowego musi być typem całkowitym, zgodnie z opisem w [podstawowych typów](../cpp/fundamental-types-cpp.md).  
  
## <a name="restrictions-on-bit-fields"></a>Ograniczenia dotyczące pól bitowych  
 Poniżej przedstawiono szczegóły błędnego operacje na pól bitowych:  
  
1.  Pobieranie adresu pola bitowego.  
  
2.  Inicjowanie odwołania z polem bitowym.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasy i struktury](../cpp/classes-and-structs-cpp.md)