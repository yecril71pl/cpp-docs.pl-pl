---
title: "Ustalanie, jakiego typu metody dostępu użyć | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- rowsets [C++], data types
- accessors [C++], types
ms.assetid: 22483dd2-f4e0-4dcb-8e4d-cd43a9c1a3db
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 28173b18e1f2ab6e7c916679d5fa5a27c08caaeb
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="determining-which-type-of-accessor-to-use"></a>Ustalanie, jakiego typu metody dostępu użyć
Typy danych w zestawie wierszy można określić w czasie kompilacji lub w czasie wykonywania.  
  
 Jeśli chcesz określić typy danych w czasie kompilacji, statycznej metody dostępu użyć (takie jak `CAccessor`). Typy danych można określić ręcznie lub za pomocą biblioteki ATL OLE DB użytkownika kreatora.  
  
 Aby określić typy danych w czasie wykonywania, należy użyć dynamiczny (`CDynamicAccessor` lub jego elementach podrzędnych) lub ręczne metody dostępu (`CManualAccessor`). W takich przypadkach można wywołać `GetColumnInfo` na wierszy do zwracania informacji powiązanie kolumny, w którym można określić typy.  
  
 W poniższej tabeli wymieniono typy metod dostępu w szablony konsumentów. Każda metoda dostępu ma zalety i wady. W zależności od sytuacji jeden typ metody dostępu należy własnych potrzeb.  
  
|Klasa metody dostępu|Powiązanie|Parametr|Komentarz|  
|--------------------|-------------|---------------|-------------|  
|`CAccessor`|Utwórz rekord użytkownika z `COLUMN_ENTRY` makra. Makra powiązać element członkowski danych w tym rekordzie metodzie dostępu. Po utworzeniu zestawu wierszy kolumn nie może być zwolnione.|Tak, przy użyciu **atrybut PARAM_MAP** makro wpisu. Raz powiązania parametrów nie może być zwolnione.|Najszybszym dostępu z powodu małej ilości kodu.|  
|`CDynamicAccessor`|Automatyczne.|Nie.|Przydatne, jeśli nie jest znany typ danych w zestawie wierszy.|  
|`CDynamicParameterAccessor`|Automatyczne, ale może być [przesłonięcia](../../data/oledb/overriding-a-dynamic-accessor.md).|Tak, jeśli dostawca obsługuje `ICommandWithParameters`. Parametry powiązane automatycznie.|Wolniej niż `CDynamicAccessor` ale przydatne w przypadku wywoływania procedury składowanej ogólne.|  
|**CDynamicStringAccessor[A,W]**|Automatyczne.|Nie.|Pobiera dane uzyskiwane ze źródła danych jako dane ciągu.|  
|`CManualAccessor`|Ręczne przy użyciu `AddBindEntry`.|Ręcznie przy użyciu `AddParameterEntry`.|Bardzo szybko; Parametry i kolumny powiązane tylko raz. Należy określić typ danych do użycia. (Zobacz [DBVIEWER](http://msdn.microsoft.com/en-us/07620f99-c347-4d09-9ebc-2459e8049832) przykładowa, np.) Wymaga większej ilości kodu niż `CDynamicAccessor` lub `CAccessor`. Jest kilka dodatkowych bezpośrednie wywoływanie OLE DB.|  
|`CXMLAccessor`|Automatyczne.|Nie.|Pobiera dane uzyskiwane ze źródła danych jako ciągu dane i formatuje go jako oznakowane XML dane.|  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z metod dostępu](../../data/oledb/using-accessors.md)