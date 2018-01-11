---
title: "Alokowanie i zwalnia pamięć dla typu BSTR | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: bstr
dev_langs: C++
helpviewer_keywords:
- BSTRs, memory allocation
- memory deallocation, string memory
- memory [C++], releasing
- memory allocation, BSTRs
- memory deallocation, BSTR memory
- strings [C++], releasing
ms.assetid: 98041e29-3442-4a02-b425-7a4a13e9cc84
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 282ceac05587452fad750f05b642c0ffd5b929a7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="allocating-and-releasing-memory-for-a-bstr"></a>Alokowanie i zwalnia pamięć dla typu BSTR
Po utworzeniu `BSTR`s i przekazać je między obiektami COM, użytkownik musi należy ostrożnie traktowanie pamięci ich użyć w celu uniknięcia przecieki pamięci. Gdy `BSTR` pozostaje w interfejsie, należy zwolnić pamięci po zakończeniu z nim. Jednakże, gdy `BSTR` przekazuje z interfejsu, odbierająca obiekt bierze odpowiedzialność za jego zarządzania pamięcią.  
  
 Ogólnie rzecz biorąc, reguły podziału i zwalnia pamięć przydzielona dla `BSTR`s są następujące:  
  
-   Podczas wywoływania funkcji, która oczekuje `BSTR` argumentu, należy przydzielić pamięci dla `BSTR` przed wywołaniem i zwolnij go później. Na przykład:  
  
     [!code-cpp[NVC_ATLMFC_Utilities#192](../atl-mfc-shared/codesnippet/cpp/allocating-and-releasing-memory-for-a-bstr_1.cpp)]  
  
     [!code-cpp[NVC_ATLMFC_Utilities#193](../atl-mfc-shared/codesnippet/cpp/allocating-and-releasing-memory-for-a-bstr_2.cpp)]  
  
-   Podczas wywoływania funkcji zwracającej `BSTR`, ciąg należy zwolnić samodzielnie. Na przykład:  
  
     [!code-cpp[NVC_ATLMFC_Utilities#194](../atl-mfc-shared/codesnippet/cpp/allocating-and-releasing-memory-for-a-bstr_3.cpp)]  
  
     [!code-cpp[NVC_ATLMFC_Utilities#195](../atl-mfc-shared/codesnippet/cpp/allocating-and-releasing-memory-for-a-bstr_4.cpp)]  
  
-   Gdy wdrożenie funkcją, która zwraca `BSTR`, Przydziel ciąg, ale nie zwolnienia. Odbieranie funkcji zwalnia pamięć. Na przykład:  
  
     [!code-cpp[NVC_ATLMFC_Utilities#196](../atl-mfc-shared/codesnippet/cpp/allocating-and-releasing-memory-for-a-bstr_5.cpp)]  
  
## <a name="see-also"></a>Zobacz też  
 [Ciągi (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)   
 [CStringT::AllocSysString](../atl-mfc-shared/reference/cstringt-class.md#allocsysstring)   
 [SysAllocString](https://msdn.microsoft.com/library/windows/desktop/ms221458.aspx)   
 [SysFreeString](https://msdn.microsoft.com/library/windows/desktop/ms221481.aspx)

