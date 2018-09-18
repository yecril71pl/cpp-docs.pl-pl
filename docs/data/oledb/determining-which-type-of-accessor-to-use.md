---
title: Ustalanie, jakiego typu metody dostępu użyć | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- rowsets [C++], data types
- accessors [C++], types
ms.assetid: 22483dd2-f4e0-4dcb-8e4d-cd43a9c1a3db
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 720a72406bec5672757c1b2c5713586b7fc7f1ca
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46086970"
---
# <a name="determining-which-type-of-accessor-to-use"></a>Ustalanie, jakiego typu metody dostępu użyć

W czasie kompilacji lub w czasie wykonywania, można określić typy danych w zestawie wierszy.  
  
Jeśli potrzebujesz określić typy danych w czasie kompilacji, należy użyć statycznej metody dostępu (takich jak `CAccessor`). Typy danych można określić ręcznie lub przy użyciu biblioteki ATL OLE DB Kreator konsumenta.  
  
Jeśli potrzebujesz określić typy danych w czasie wykonywania, użyj dynamiczny (`CDynamicAccessor` lub jego elementy podrzędne) lub ręczne metody dostępu (`CManualAccessor`). W takich przypadkach można wywołać `GetColumnInfo` na wierszy, aby zwrócić informacje o powiązaniu kolumny, z której można określić typy.  
  
W poniższej tabeli wymieniono typy metod dostępu w szablonami konsumentów. Metoda dostępu do każdego ma zalety i wady. W zależności od sytuacji jeden typ metody dostępu powinny odpowiadać Twoim potrzebom.  
  
|Klasa metody dostępu|Powiązanie|Parametr|Komentarz|  
|--------------------|-------------|---------------|-------------|  
|`CAccessor`|Utwórz rekord użytkownika za pomocą makra COLUMN_ENTRY. Makra powiązać element członkowski danych rekordu akcesor. Po utworzeniu zestawu wierszy kolumn nie może być zwolnione.|Tak, przy użyciu wpisu — makro PARAM_MAP. Raz powiązania parametrów nie może być zwolnione.|Metoda najszybszy dostępu z powodu małej ilości kodu.|  
|`CDynamicAccessor`|Automatyczne.|Nie.|Parametr jest przydatne, jeśli nie jest znany typ danych w zestawie wierszy.|  
|`CDynamicParameterAccessor`|Automatyczne, ale może być [zastąpione](../../data/oledb/overriding-a-dynamic-accessor.md).|Tak, jeśli dostawca obsługuje `ICommandWithParameters`. Automatycznie wiązania parametrów.|Wolniejsza niż `CDynamicAccessor` ale przydatne w przypadku wywoływania ogólnych procedurach składowanych.|  
|`CDynamicStringAccessor[A,W]`|Automatyczne.|Nie.|Pobiera dane otwierane z magazynu danych jako dane ciągu.|  
|`CManualAccessor`|Ręczne przy użyciu `AddBindEntry`.|Ręcznie przy użyciu `AddParameterEntry`.|Bardzo szybko; Parametry i kolumny powiązane tylko raz. Należy określić typ danych do użycia. (Zobacz [DBVIEWER](https://github.com/Microsoft/VCSamples) próbki, na przykład.) Wymaga większej ilości kodu niż `CDynamicAccessor` lub `CAccessor`. Istnieje bardziej bezpośrednie wywoływanie OLE DB.|  
|`CXMLAccessor`|Automatyczne.|Nie.|Pobiera dane otwierane z magazynu danych jako dane ciągu i formatuje ją danych oznaczone jako XML.|  
  
## <a name="see-also"></a>Zobacz też  

[Korzystanie z metod dostępu](../../data/oledb/using-accessors.md)