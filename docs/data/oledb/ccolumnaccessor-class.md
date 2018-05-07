---
title: Ccolumnaccessor — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CColumnAccessor
- ATL::CColumnAccessor
- ATL.CColumnAccessor
dev_langs:
- C++
helpviewer_keywords:
- CColumnAccessor class
ms.assetid: 6ce1e67f-6a20-490d-9326-c168b43eee7e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 8d211277a8354d94f1892b97ea8f808cc0b22c30
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="ccolumnaccessor-class"></a>CColumnAccessor — Klasa
Generuje kod wprowadzony konsumenta.  
  
## <a name="syntax"></a>Składnia

```cpp
class CColumnAccessor : public CAccessorBase  
```  
  
## <a name="remarks"></a>Uwagi  
 Wprowadzony kod każdej kolumny jest powiązana jako osobne metody dostępu. Należy pamiętać, że ta klasa jest używana w wprowadzony kod (na przykład mogą wystąpić go podczas debugowania), ale zwykle nie trzeba korzystać bezpośrednio lub jego metody.  
  
 `CColumnAccessor` implementuje następujące metody klasy zastępczej, z których każdy odpowiada funkcji do innych metod klasy dostępu:  
  
-   `CColumnAccessor` Konstruktor; Tworzy i inicjuje `CColumnAccessor` obiektu.  
  
-   `CreateAccessor` Przydziela pamięć dla kolumny struktury powiązania i inicjuje elementów członkowskich danych kolumny.  
  
-   **BindColumns** wiąże kolumn metody dostępu.  
  
-   **SetParameterBuffer** przydziela buforów dla parametrów.  
  
-   `AddParameter` Dodaje wpis parametru do struktury zapis parametru.  
  
-   **HasOutputColumns** Określa, czy akcesor ma produkt wyjściowy kolumn  
  
-   **HasParameters** Określa, czy akcesor ma parametrów.  
  
-   `BindParameters` Wiąże utworzony parametry kolumny.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbcli.h  
  
## <a name="see-also"></a>Zobacz też  
 [Szablony konsumentów OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Szablony konsumentów OLE DB — dokumentacja](../../data/oledb/ole-db-consumer-templates-reference.md)