---
title: Przekazywanie testów zgodności z OLE DB | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- testing, OLE DB providers
- testing providers
- conformance testing
- conformance testing [OLE DB]
- OLE DB providers, testing
ms.assetid: d1a4f147-2edd-476c-b452-0e6a0ac09891
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 2be281252bc9166473eeb5d0e57a509941ad3673
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50057806"
---
# <a name="passing-ole-db-conformance-tests"></a>Przechodzenie testów zgodności z OLE DB

Aby dostawców bardziej spójną, Data Access SDK zawiera zestaw testów zgodności z OLE DB. Testy Sprawdź wszystkie aspekty dostawcą i zapewniają wystarczającą pewność, że dostawca funkcji jako oczekiwana. Testów zgodności z OLE DB można znaleźć na Microsoft Data Access SDK. Ta sekcja koncentruje się na elementy, które należy wykonać, aby pomyślnie przejść testy zgodności. Aby uzyskać informacje na temat uruchamiania testów zgodności z OLE DB zobacz zestaw SDK.

## <a name="running-the-conformance-tests"></a>Uruchamianie testów zgodności

W Visual C++ 6.0 szablony dostawców OLE DB dodano wiele funkcji podłączania pozwala sprawdzić właściwości i wartości. Większość tych funkcji dodanych w odpowiedzi na testów zgodności.

> [!NOTE]
> Musisz dodać kilka funkcji sprawdzania poprawności dla dostawcy do przekazania testów zgodności z OLE DB.

Ten dostawca wymaga dwóch procedur weryfikacji. Pierwszy procedury `CRowsetImpl::ValidateCommandID`, jest częścią klasy zestawu wierszy. Wywoływana podczas tworzenia zestawu wierszy za pomocą szablonów dostawcy. W przykładzie użyto tej procedury do Poinformuj klientów, że nie obsługuje indeksów. Pierwsze wywołanie jest `CRowsetImpl::ValidateCommandID` (należy pamiętać, że dostawca używa `_RowsetBaseClass` typedef dodany do mapy interfejsu dla `CCustomRowset` w [Obsługa dostawców dla zakładek](../../data/oledb/provider-support-for-bookmarks.md), więc nie trzeba wpisywać tego długi wiersz szablonu argumenty). Następnie zwraca DB_E_NOINDEX, jeśli parametr indeksu nie jest NULL (oznacza to, użytkownik chce użyć indeksu na NAS). Aby uzyskać więcej informacji na temat identyfikatorów poleceń, zobacz specyfikację OLE DB i poszukaj `IOpenRowset::OpenRowset`.

Poniższy kod jest `ValidateCommandID` procedurze weryfikacji:

```cpp
/////////////////////////////////////////////////////////////////////
// CustomRS.H
// Class: CCustomRowset

HRESULT ValidateCommandID(DBID* pTableID, DBID* pIndexID)
{
   HRESULT hr = _RowsetBaseClass::ValidateCommandID(pTableID, pIndexID);
   if (hr != S_OK)
      return hr;

   if (pIndexID != NULL)
      return DB_E_NOINDEX;    // Doesn't support indexes

   return S_OK;
}
```

Wywołanie szablony dostawcy `OnPropertyChanged` metody zawsze wtedy, gdy ktoś zmieni się właściwość w `DBPROPSET_ROWSET` grupy. Jeśli chcesz obsługiwać właściwości dla innych grup, możesz dodać je do odpowiedniego obiektu (czyli `DBPROPSET_SESSION` kontroli go w programie `CCustomSession` klasy).

Ten kod najpierw sprawdza, czy właściwość jest połączone z innym. Jeśli ta właściwość jest powiązane, ustawia `DBPROP_BOOKMARKS` właściwość `True`. Dodatek C specyfikacji OLE DB zawiera informacje dotyczące właściwości. Te informacje również informuje, czy właściwość jest powiązany inny.

Można także dodać `IsValidValue` rutynowej w kodzie. Wywołanie szablony `IsValidValue` podczas próby ustawienia właściwości. Czy zastąpić tę metodę, jeśli potrzebujesz dodatkowego przetwarzania podczas ustawiania wartości właściwości. Może mieć jedną z następujących metod dla każdego zestawu właściwości.

## <a name="see-also"></a>Zobacz też

[Zaawansowane techniki dostawcy](../../data/oledb/advanced-provider-techniques.md)