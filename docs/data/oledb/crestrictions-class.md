---
title: Klasa CRestrictions | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL::CRestrictions
- CRestrictions
- ATL.CRestrictions
- CRestrictions.Open
- ATL::CRestrictions::Open
- ATL.CRestrictions.Open
- CRestrictions::Open
dev_langs:
- C++
helpviewer_keywords:
- CRestrictions class
- Open method
ms.assetid: 0aaa2364-641c-4318-b110-7446aada4b4f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 2e850b5ebad231b07ce7d6c7dca79126a9b2ba15
ms.sourcegitcommit: 3a141cf07b5411d5f1fdf6cf67c4ce928cf389c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/11/2018
ms.locfileid: "49082361"
---
# <a name="crestrictions-class"></a>Klasa CRestrictions

Ogólna klasa, która pozwala określić ograniczenia dla zestawów wierszy schematu.  
  
## <a name="syntax"></a>Składnia

```cpp
template <class T, short nRestrictions, const GUID* pguid>  
class CRestrictions : 
   public CSchemaRowset <T, nRestrictions>  
```  
  
### <a name="parameters"></a>Parametry  

*T*<br/>
Klasa, używane do dostępu.  
  
*nRestrictions*<br/>
Liczba kolumn ograniczeń dla zestawu wierszy schematu.  
  
*pguid*<br/>
Wskaźnik do identyfikatora GUID dla schematu.  

## <a name="requirements"></a>Wymagania  

**Nagłówek:** atldbsch.h 
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[Otwórz](#open)|Zwraca wynik ustawione zgodnie z ograniczeniami dostarczone przez użytkownika.|   

## <a name="open"></a> CRestrictions::Open

Zwraca wynik ustawione zgodnie z ograniczeniami dostarczone przez użytkownika.  
  
### <a name="syntax"></a>Składnia  
  
```cpp
HRESULT Open(const CSession& session,  
   LPCTSTR lpszParam 1 = NULL,  
   LPCTSTR lpszParam 2 = NULL,  
   LPCTSTR lpszParam 3 = NULL,  
   LPCTSTR lpszParam 4 = NULL,  
   LPCTSTR lpszParam 5 = NULL,  
   LPCTSTR lpszParam 6 = NULL,  
   LPCTSTR lpszParam 7 = NULL,  
   bool bBind = true);  
```  
  
#### <a name="parameters"></a>Parametry  

*Sesji*<br/>
[in] Określa istniejącego obiektu sesji używane do połączenia ze źródłem danych.  
  
*lpszParam*<br/>
[in] Określa ograniczenia na zestaw wierszy schematu.  
  
*bBind*<br/>
[in] Określa, czy należy automatycznie powiązania na mapie kolumny. Wartość domyślna to **true**, co powoduje, że mapa kolumny z oświadczeniem automatycznie. Ustawienie *bBind* do **false** uniemożliwia automatyczne powiązania mapy kolumnę tak, aby można powiązać ręcznie. (Ręczne powiązanie to szczególne znaczenie w odniesieniu do użytkowników OLAP).  
  
### <a name="return-value"></a>Wartość zwracana  

Jedna z wartości HRESULT standardowych.  
  
### <a name="remarks"></a>Uwagi  

Można określić maksymalnie siedem ograniczeń w zestawie wierszy schematu.  
  
Zobacz [IDBSchemaRowset](/previous-versions/windows/desktop/ms713686) informacji o zdefiniowanych ograniczenia na każdy zestaw wierszy schematu.  
  
## <a name="see-also"></a>Zobacz też  

[Szablony konsumentów OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Szablony konsumentów OLE DB — dokumentacja](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[Klasy zestawów wierszy schematu i klasy Typedef](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)