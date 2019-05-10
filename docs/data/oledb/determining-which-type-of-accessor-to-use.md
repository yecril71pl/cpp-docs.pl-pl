---
title: Ustalanie, jakiego typu metody dostępu użyć
ms.date: 05/09/2019
helpviewer_keywords:
- rowsets [C++], data types
- accessors [C++], types
ms.assetid: 22483dd2-f4e0-4dcb-8e4d-cd43a9c1a3db
ms.openlocfilehash: f32b3375a517c8716324a2d5b35ec16826605f8e
ms.sourcegitcommit: 00e26915924869cd7eb3c971a7d0604388abd316
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/10/2019
ms.locfileid: "65525089"
---
# <a name="determining-which-type-of-accessor-to-use"></a>Ustalanie, jakiego typu metody dostępu użyć

W czasie kompilacji lub w czasie wykonywania, można określić typy danych w zestawie wierszy.

Jeśli potrzebujesz określić typy danych w czasie kompilacji, należy użyć statycznej metody dostępu (takich jak `CAccessor`). 

Jeśli potrzebujesz określić typy danych w czasie wykonywania, użyj dynamiczny (`CDynamicAccessor` lub jego elementy podrzędne) lub ręczne metody dostępu (`CManualAccessor`). W takich przypadkach można wywołać `GetColumnInfo` na wierszy, aby zwrócić informacje o powiązaniu kolumny, z której można określić typy.

W poniższej tabeli wymieniono typy metod dostępu w szablonami konsumentów. Metoda dostępu do każdego ma zalety i wady. W zależności od sytuacji jeden typ metody dostępu powinny odpowiadać Twoim potrzebom.

|Klasa metody dostępu|Wiązanie|Parametr|Komentarz|
|--------------------|-------------|---------------|-------------|
|`CAccessor`|Utwórz rekord użytkownika za pomocą makra COLUMN_ENTRY. Makra powiązać element członkowski danych rekordu akcesor. Po utworzeniu zestawu wierszy kolumn nie może być zwolnione.|Tak, przy użyciu wpisu — makro PARAM_MAP. Raz powiązania parametrów nie może być zwolnione.|Metoda najszybszy dostępu z powodu małej ilości kodu.|
|`CDynamicAccessor`|Automatyczne.|Nie.|Parametr jest przydatne, jeśli nie znasz typu danych w zestawie wierszy.|
|`CDynamicParameterAccessor`|Automatyczne, ale może być [zastąpione](../../data/oledb/overriding-a-dynamic-accessor.md).|Tak, jeśli dostawca obsługuje `ICommandWithParameters`. Automatycznie wiązania parametrów.|Wolniejsza niż `CDynamicAccessor` ale przydatne w przypadku wywoływania ogólnych procedurach składowanych.|
|`CDynamicStringAccessor[A,W]`|Automatyczne.|Nie.|Pobiera dane otwierane z magazynu danych jako dane ciągu.|
|`CManualAccessor`|Ręczne przy użyciu `AddBindEntry`.|Ręcznie przy użyciu `AddParameterEntry`.|Szybko; Parametry i kolumny powiązane tylko raz. Należy określić typ danych do użycia. (Zobacz [DBVIEWER](https://github.com/Microsoft/VCSamples) próbki, na przykład.) Wymaga większej ilości kodu niż `CDynamicAccessor` lub `CAccessor`. Istnieje bardziej bezpośrednie wywoływanie OLE DB.|
|`CXMLAccessor`|Automatyczne.|Nie.|Pobiera dane otwierane z magazynu danych jako dane ciągu i formatuje ją danych oznaczone jako XML.|

## <a name="see-also"></a>Zobacz także

[Korzystanie z metod dostępu](../../data/oledb/using-accessors.md)