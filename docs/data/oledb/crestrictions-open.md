---
title: CRestrictions::Open | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CRestrictions.Open
- ATL::CRestrictions::Open
- ATL.CRestrictions.Open
- CRestrictions::Open
dev_langs: C++
helpviewer_keywords: Open method
ms.assetid: 0aff0cc3-543a-47d2-8d6b-ebb36926b6db
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: bbb0b175a6fa5a6cf93b4fe107884d5bb84f2487
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="crestrictionsopen"></a>CRestrictions::Open
Zwraca wynik ustawiony odpowiednio do atrybutów ograniczenia dostarczone przez użytkownika.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      HRESULT Open(  
   const CSession& session,  
   LPCTSTR lpszParam 1 = NULL,  
   LPCTSTR lpszParam 2 = NULL,  
   LPCTSTR lpszParam 3 = NULL,  
   LPCTSTR lpszParam 4 = NULL,  
   LPCTSTR lpszParam 5 = NULL,  
   LPCTSTR lpszParam 6 = NULL,  
   LPCTSTR lpszParam 7 = NULL,  
   bool bBind = true  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `session`  
 [in] Określa istniejący obiekt sesji używane do łączenia się ze źródłem danych.  
  
 *lpszParam*  
 [in] Określa ograniczenia na zestaw wierszy schematu.  
  
 `bBind`  
 [in] Określa, czy automatycznie powiązać mapowania kolumn. Wartość domyślna to **true**, co powoduje, że mapowania kolumn powiązać automatycznie. Ustawienie `bBind` do **false** uniemożliwia automatyczne powiązanie mapowania kolumn, dzięki czemu można powiązać ręcznie. (Ręczne powiązanie jest znaczący użytkownikom OLAP).  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeden standardowy `HRESULT` wartości.  
  
## <a name="remarks"></a>Uwagi  
 Można określić maksymalnie siedem ograniczeń w zestawie wierszy schematu.  
  
 Zobacz [IDBSchemaRowset](https://msdn.microsoft.com/en-us/library/ms713686.aspx) dla informacji na temat ograniczeń zdefiniowanych w każdym wierszy schematu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbsch.h  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CRestrictions](../../data/oledb/crestrictions-class.md)   
 [Klasy zestawów wierszy schematu i klasy Typedef](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)