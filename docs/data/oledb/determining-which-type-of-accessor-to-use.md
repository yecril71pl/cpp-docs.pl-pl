---
title: Ustalanie, jakiego typu metody dostępu użyć
ms.date: 05/09/2019
helpviewer_keywords:
- rowsets [C++], data types
- accessors [C++], types
ms.assetid: 22483dd2-f4e0-4dcb-8e4d-cd43a9c1a3db
ms.openlocfilehash: 31efa36bcd61caa154cd3e4c147ad5ed8728b04c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80210993"
---
# <a name="determining-which-type-of-accessor-to-use"></a>Ustalanie, jakiego typu metody dostępu użyć

Można określić typy danych w zestawie wierszy w czasie kompilacji lub w czasie wykonywania.

Jeśli musisz określić typy danych w czasie kompilacji, użyj statycznej metody dostępu (takiej jak `CAccessor`).

Jeśli musisz określić typy danych w czasie wykonywania, użyj dynamicznej (`CDynamicAccessor` lub jego elementów podrzędnych) lub metody dostępu ręcznego (`CManualAccessor`). W takich przypadkach można wywołać `GetColumnInfo` w zestawie wierszy, aby zwrócić informacje o powiązaniu kolumny, z których można określić typy.

Poniższa tabela zawiera listę typów metod dostępu udostępnianych w szablonach odbiorców. Każdy akcesor ma zalety i wady. W zależności od sytuacji jeden typ metody dostępu powinien odpowiadać Twoim potrzebom.

|Klasa akcesora|Powiązanie|Parametr|Komentarz|
|--------------------|-------------|---------------|-------------|
|`CAccessor`|Utwórz rekord użytkownika przy użyciu makr COLUMN_ENTRY. Makra powiążą element członkowski danych w tym rekordzie z akcesorem. Podczas tworzenia zestawu wierszy nie można powiązać kolumn.|Tak, przy użyciu wpisu makra PARAM_MAP. Po powiązaniu parametrów nie można ich powiązać.|Najszybsze metody dostępu z powodu niewielkiej ilości kodu.|
|`CDynamicAccessor`|Automatyczne.|Nie.|Przydatne, jeśli nie znasz typu danych w zestawie wierszy.|
|`CDynamicParameterAccessor`|Automatyczne, ale można je [zastąpić](../../data/oledb/overriding-a-dynamic-accessor.md).|Tak, jeśli dostawca obsługuje `ICommandWithParameters`. Parametry są powiązane automatycznie.|Wolniejsze niż `CDynamicAccessor`, ale przydatne do wywoływania ogólnych procedur składowanych.|
|`CDynamicStringAccessor[A,W]`|Automatyczne.|Nie.|Pobiera dane, do których można uzyskać dostęp z magazynu danych jako dane ciągu.|
|`CManualAccessor`|Ręczne używanie `AddBindEntry`.|Ręczne używanie `AddParameterEntry`.|Fast parametry i kolumny są powiązane tylko raz. Należy określić typ danych, które mają być używane. (Zobacz przykład [DBviewer](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Consumer) przykłady). Wymaga więcej kodu niż `CDynamicAccessor` lub `CAccessor`. Jest to bardziej podobne do wywoływania OLE DB bezpośrednio.|
|`CXMLAccessor`|Automatyczne.|Nie.|Pobiera dane, do których uzyskuje się dostęp z magazynu danych jako dane ciągów i formatuje je jako dane oznakowane XML.|

## <a name="see-also"></a>Zobacz też

[Korzystanie z metod dostępu](../../data/oledb/using-accessors.md)
