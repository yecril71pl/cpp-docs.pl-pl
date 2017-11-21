---
title: "Inicjowanie aparatu bazy danych DAO i kończenie działania | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.mfc.macros.data
dev_langs: C++
helpviewer_keywords:
- DAO (Data Access Objects), termination
- DAO (Data Access Objects), initialization
ms.assetid: a7edf31c-e7c2-4f3e-aada-63c3e48781da
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 4e32930b53c6e05abf692474fdb1236fe007a1eb
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="dao-database-engine-initialization-and-termination"></a>Inicjowanie i kończenie działania aparatu bazy danych DAO
Korzystając z obiektów MFC DAO, aparatu bazy danych DAO najpierw należy zainicjować i następnie zakończona przed kończy działanie aplikacji lub biblioteki DLL. Dwie funkcje `AfxDaoInit` i `AfxDaoTerm`, wykonać te zadania.  
  
### <a name="dao-database-engine-initialization-and-termination"></a>Inicjowanie i kończenie działania aparatu bazy danych DAO  
  
|||  
|-|-|  
|[Afxdaoinit —](#afxdaoinit)|Aparat bazy danych DAO.|  
|[Afxdaoterm —](#afxdaoterm)|Kończy aparatu bazy danych DAO.|  
  
##  <a name="afxdaoinit"></a>Afxdaoinit —  
 Ta funkcja inicjuje aparatu bazy danych DAO.  
  
```  
 
void AfxDaoInit();

throw(CDaoException*);  
```  
  
### <a name="remarks"></a>Uwagi  
 W większości przypadków, nie trzeba wywołać `AfxDaoInit` ponieważ aplikacja wywołuje z go automatycznie, gdy jest to potrzebne.  
  
 Powiązane informacje, a na przykład wywołanie `AfxDaoInit`, zobacz [54 Uwaga techniczna](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md).  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxdao.h  
  
##  <a name="afxdaoterm"></a>Afxdaoterm —  
 Ta funkcja kończy aparatu bazy danych DAO.  
  
```  
 
void AfxDaoTerm();  
```  
  
### <a name="remarks"></a>Uwagi  
 Zazwyczaj konieczne jest wywołanie tej funkcji w zwykły biblioteki MFC DLL; Aplikacja zostanie automatycznie wywołać `AfxDaoTerm` gdy jest to potrzebne.  
  
 Regularne biblioteki DLL MFC wywołać `AfxDaoTerm` przed `ExitInstance` funkcji, ale po wszystkich obiektów MFC DAO zostały zniszczone.  
  
 Aby uzyskać odpowiednie informacje, zobacz [54 Uwaga techniczna](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md).  

### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxdao.h  

## <a name="see-also"></a>Zobacz też  
 [Makra i funkcje globalne](../../mfc/reference/mfc-macros-and-globals.md)
