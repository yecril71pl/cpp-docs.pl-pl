---
title: "Icommandtextimpl — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ICommandText
dev_langs:
- C++
helpviewer_keywords:
- ICommandText class
ms.assetid: 9c2715cc-1e55-4468-8327-85341617ed46
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: c74ad1da299c05ade422596b08d48f33f9d22e37
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="icommandtextimpl-class"></a>ICommandTextImpl — Klasa
Udostępnia implementację dla [ICommandText](https://msdn.microsoft.com/en-us/library/ms714914.aspx) interfejsu.  
  
## <a name="syntax"></a>Składnia

```cpp
template <class T >  
class ATL_NO_VTABLE ICommandTextImpl   
   : public ICommandImpl<T, ICommandText>  
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Polecenie klasą pochodną **icommandtextimpl —**.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="interface-methods"></a>Metody interfejsu  
  
|||  
|-|-|  
|[GetCommandText](../../data/oledb/icommandtextimpl-getcommandtext.md)|Zwraca tekst polecenia ustawione przez ostatnie wywołanie [SetCommandText](../../data/oledb/icommandtextimpl-setcommandtext.md).|  
|[SetCommandText](../../data/oledb/icommandtextimpl-setcommandtext.md)|Ustawia tekst polecenia, zastępując istniejący tekst polecenia.|  
  
### <a name="data-members"></a>Elementy członkowskie danych  
  
|||  
|-|-|  
|[m_strCommandText](../../data/oledb/icommandtextimpl-m-strcommandtext.md)|Przechowuje tekst polecenia.|  
  
## <a name="remarks"></a>Uwagi  
 Interfejs obowiązkowy poleceń.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** altdb.h  
  
## <a name="see-also"></a>Zobacz też  
 [Szablony dostawców OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)