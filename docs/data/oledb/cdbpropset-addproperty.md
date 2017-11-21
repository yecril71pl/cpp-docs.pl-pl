---
title: CDBPropSet::AddProperty | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CDBPropSet::AddProperty
- CDBPropSet.AddProperty
- AddProperty
- ATL::CDBPropSet::AddProperty
- ATL.CDBPropSet.AddProperty
dev_langs: C++
helpviewer_keywords: AddProperty method
ms.assetid: dc9539d3-1ee4-40f3-9281-2068e6d65e93
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 206bc229de3de55d58121e10e1fa6f80cb7b48a4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="cdbpropsetaddproperty"></a>CDBPropSet::AddProperty
Dodaje właściwość do zestawu właściwości.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      bool AddProperty(   
   DWORD dwPropertyID,   
   const VARIANT& var,   
   DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED    
) throw( );  
bool AddProperty(  
   DWORD dwPropertyID,  
   LPCSTR szValue,  
   DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED    
) throw( );  
bool AddProperty(  
   DWORD dwPropertyID,  
   LPCWSTR szValue,   
   DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED    
) throw( );  
bool AddProperty(  
   DWORD dwPropertyID,  
   bool bValue,  
   DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED    
) throw( );  
bool AddProperty(  
   DWORD dwPropertyID,  
   BYTE bValue,  
   DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED    
);  
bool AddProperty(  
   DWORD dwPropertyID,  
   short nValue,  
   DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED    
);  
bool AddProperty(  
   DWORD dwPropertyID,  
   long nValue,  
   DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED    
);  
bool AddProperty(  
   DWORD dwPropertyID,  
   float fltValue,  
   DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED    
);  
bool AddProperty(  
   DWORD dwPropertyID,  
   double dblValue,  
   DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED    
) throw( );  
bool AddProperty(  
   DWORD dwPropertyID,  
   CY cyValue,  
   DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED    
) throw( );  
```  
  
#### <a name="parameters"></a>Parametry  
 *dwPropertyID*  
 [in] Identyfikator właściwości do dodania. Używany do inicjowania **dwPropertyID** z `DBPROP` struktury dodać do zbioru właściwości.  
  
 `var`  
 [in] Wariant używaną do inicjalizacji wartości właściwości dla `DBPROP` struktury dodać do zbioru właściwości.  
  
 `szValue`  
 [in] Ciąg używany do inicjowania wartości właściwości dla `DBPROP` struktury dodać do zbioru właściwości.  
  
 `bValue`  
 [in] A **BAJTÓW** lub wartość logiczną używaną do inicjalizacji wartości właściwości dla `DBPROP` struktury dodać do zbioru właściwości.  
  
 `nValue`  
 [in] Wartość całkowita używaną do inicjalizacji wartości właściwości dla `DBPROP` struktury dodać do zbioru właściwości.  
  
 *fltValue*  
 [in] Wartość zmiennoprzecinkowa używaną do inicjalizacji wartości właściwości dla `DBPROP` struktury dodać do zbioru właściwości.  
  
 `dblValue`  
 [in] Używany do inicjowania wartości właściwości dla wartości zmiennoprzecinkowej podwójnej precyzji `DBPROP` struktury dodać do zbioru właściwości.  
  
 `cyValue`  
 [in] Używany do inicjowania wartości właściwości dla wartości waluty CY `DBPROP` struktury dodać do zbioru właściwości.  
  
## <a name="return-value"></a>Wartość zwracana  
 **wartość true,** Jeśli właściwość została pomyślnie dodana. W przeciwnym razie **false**.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbcli.h  
  
## <a name="see-also"></a>Zobacz też  
 [Cdbpropset — klasa](../../data/oledb/cdbpropset-class.md)   
 [Struktura DBPROP](https://msdn.microsoft.com/en-us/library/ms717970.aspx)