---
title: CDBPropSet::AddProperty | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CDBPropSet::AddProperty
- CDBPropSet.AddProperty
- AddProperty
- ATL::CDBPropSet::AddProperty
- ATL.CDBPropSet.AddProperty
dev_langs:
- C++
helpviewer_keywords:
- AddProperty method
ms.assetid: dc9539d3-1ee4-40f3-9281-2068e6d65e93
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 454d86b7c5b654ac1af5b628abc5db7d3678d2f2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="cdbpropsetaddproperty"></a>CDBPropSet::AddProperty
Dodaje właściwość do zestawu właściwości.  
  
## <a name="syntax"></a>Składnia  
  
```
bool AddProperty(DWORD dwPropertyID,   
   constVARIANT& var,   
   DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED) throw();bool AddProperty(DWORD dwPropertyID,  
   LPCSTR szValue,  DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED) throw();bool AddProperty(DWORD dwPropertyID,  
   LPCWSTR szValue,DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED) throw();bool AddProperty(DWORD dwPropertyID,  
   bool bValue,  DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED) throw();bool AddProperty(DWORD dwPropertyID,  
   BYTE bValue,  DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED);bool AddProperty(DWORD dwPropertyID,  
   short nValue,  DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED);bool AddProperty(DWORD dwPropertyID,  
   long nValue,  DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED);bool AddProperty(DWORD dwPropertyID,  
   float fltValue,  DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED);bool AddProperty(DWORD dwPropertyID,  
   double dblValue,  DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED) throw();bool AddProperty(DWORD dwPropertyID,  
   CY cyValue,  DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED) throw();  
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