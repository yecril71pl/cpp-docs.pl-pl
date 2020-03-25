---
title: Konwertowanie danych nieobsługiwanych przez dostawcę
ms.date: 10/29/2018
helpviewer_keywords:
- OLE DB provider templates, unsupported data types
ms.assetid: f495e50f-530a-4fab-ab54-e0c359785845
ms.openlocfilehash: e87aebc4d6f23343af9a2f966d2c522e95b304ea
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80211500"
---
# <a name="converting-data-not-supported-by-the-provider"></a>Konwertowanie danych nieobsługiwanych przez dostawcę

Gdy odbiorca zażąda typu danych, który nie jest obsługiwany przez dostawcę, kod szablonu dostawcy OLE DB dla `IRowsetImpl::GetData` wywołuje Msdadc. dll w celu przekonwertowania typu danych.

W przypadku zaimplementowania interfejsu, takiego jak `IRowsetChange`, który wymaga konwersji danych, można wywołać Msdaenum. dll w celu wykonania konwersji. Użyj `GetData`, zdefiniowanego w ATLDB. h, jako przykładu.

## <a name="see-also"></a>Zobacz też

[Praca z szablonami dostawców OLE DB](../../data/oledb/working-with-ole-db-provider-templates.md)
