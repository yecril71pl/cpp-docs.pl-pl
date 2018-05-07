---
title: Inicjowanie aparatu bazy danych DAO i kończenie działania | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.mfc.macros.data
dev_langs:
- C++
helpviewer_keywords:
- DAO (Data Access Objects), termination
- DAO (Data Access Objects), initialization
ms.assetid: a7edf31c-e7c2-4f3e-aada-63c3e48781da
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3f28c0c166bcbf13181161d6afce484fe4a45b80
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="dao-database-engine-initialization-and-termination"></a>Inicjowanie i kończenie działania aparatu bazy danych DAO
Korzystając z obiektów MFC DAO, aparatu bazy danych DAO najpierw należy zainicjować i następnie zakończona przed kończy działanie aplikacji lub biblioteki DLL. Dwie funkcje `AfxDaoInit` i `AfxDaoTerm`, wykonać te zadania.  
  
### <a name="dao-database-engine-initialization-and-termination"></a>Inicjowanie i kończenie działania aparatu bazy danych DAO  
  
|||  
|-|-|  
|[Afxdaoinit —](#afxdaoinit)|Aparat bazy danych DAO.|  
|[Afxdaoterm —](#afxdaoterm)|Kończy aparatu bazy danych DAO.|  
  
##  <a name="afxdaoinit"></a>  Afxdaoinit —  
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
  
##  <a name="afxdaoterm"></a>  Afxdaoterm —  
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
