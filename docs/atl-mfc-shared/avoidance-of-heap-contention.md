---
title: Unikanie stos rywalizacji | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: C++
helpviewer_keywords: heap contention
ms.assetid: 797129d7-5f8c-4b0e-8974-bb93217e9ab5
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 73858235f949c07da646944efcae6e846a96d900
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="avoidance-of-heap-contention"></a>Unikanie stos rywalizacji
Menedżerowie ciąg domyślnej zapewniane przez MFC i ATL są proste otoki na szczycie stosu globalne. Tym globalnych sterty jest całkowicie bezpieczne wątkowo, co oznacza, że wiele wątków można przydzielić i zwolnić pamięć z niego bez jednocześnie uszkodzenie sterty. Aby zapewnić bezpieczeństwo wątków sterty musi serializować dostępu do samej siebie. Zazwyczaj jest to realizowane za pomocą sekcja krytyczna lub podobny mechanizm blokowania. Zawsze, gdy dwa wątków próbuje uzyskać jednocześnie dostęp do sterty, jeden wątek jest zablokowany do momentu zakończenia żądania innego wątku. Dla wielu aplikacji ta sytuacja rzadko występuje i wpływu na wydajność mechanizmu blokującego sterty jest niewielka. Dla aplikacji, które często dostęp wiele wątków stos rywalizacji o blokadę sterty może jednak spowodować aplikacji działać wolniej niż jeśli zostały jednowątkowe (nawet na komputerach wieloprocesorowych).  
  
 Aplikacje używające [CStringT](../atl-mfc-shared/reference/cstringt-class.md) są szczególnie podatne na stos rywalizacji ponieważ operacje na `CStringT` obiekty często wymagają; Ponowna alokacja buforu ciągu.  
  
 Jednym ze sposobów złagodzić stos rywalizacji między wątkami ma Każdy wątek przydzielić ciągi ze stosu prywatne i lokalnej wątku. Tak długo, jak ciągi przydzielonych za pomocą programu przydzielania dla wątku są używane tylko w tym wątku, program przydzielania nie muszą być bezpieczne wątkowo.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono procedury wątku przydzielanej własnej prywatnej sterty z systemem innym niż wątkowo do użycia dla ciągów wątek:  
  
 [!code-cpp[NVC_ATLMFC_Utilities#182](../atl-mfc-shared/codesnippet/cpp/avoidance-of-heap-contention_1.cpp)]  
  
## <a name="comments"></a>Komentarze  
 Wiele wątków mogą być wykonywane przy użyciu tej samej procedury wątku, ale ponieważ każdy wątek ma własną sterty nie ma rywalizacji między wątkami. Ponadto fakt, że każdy stosu nie jest bezpieczne wątkowo zapewnia mierzalnych wzrost wydajności, nawet wtedy, gdy tylko jeden wątek jest uruchomiony. Jest to wynikiem stosu nie używanie kosztowne operacje blokowane do ochrony przed współbieżny dostęp.  
  
 Bardziej skomplikowane procedury wątku może być wygodną do przechowywania wskaźnik do Menedżera ciąg wątku w gnieździe (TLS) magazynu lokalnego wątku. Dzięki temu innych funkcji o nazwie przez procedurę wątku, aby otworzyć Menedżera ciąg wątku.  
  
## <a name="see-also"></a>Zobacz też  
 [Zarządzanie pamięcią z CStringT](../atl-mfc-shared/memory-management-with-cstringt.md)

