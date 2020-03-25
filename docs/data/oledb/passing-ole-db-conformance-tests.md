---
title: Przechodzenie testów zgodności z OLE DB
ms.date: 11/04/2016
helpviewer_keywords:
- testing, OLE DB providers
- testing providers
- conformance testing
- conformance testing [OLE DB]
- OLE DB providers, testing
ms.assetid: d1a4f147-2edd-476c-b452-0e6a0ac09891
ms.openlocfilehash: eda4dccda147ddd4776bb56e649f539a7550abd1
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209789"
---
# <a name="passing-ole-db-conformance-tests"></a>Przechodzenie testów zgodności z OLE DB

Aby zapewnić bardziej spójność dostawców, zestaw SDK dostępu do danych zawiera zestaw OLE DB testów zgodności. Testy sprawdzają wszystkie aspekty dostawcy i zapewniają gwarancję, że dostawca działa zgodnie z oczekiwaniami. Testy zgodności OLE DB można znaleźć w zestawie SDK dostępu do danych firmy Microsoft. Ta sekcja koncentruje się na czynnościach, które należy wykonać, aby przekazać testy zgodności. Aby uzyskać informacje o uruchamianiu testów zgodności OLE DB, zobacz zestaw SDK.

## <a name="running-the-conformance-tests"></a>Uruchamianie testów zgodności

W programie C++ Visual 6,0 szablony dostawcy OLE DB dodaliśmy wiele funkcji podłączania, aby umożliwić sprawdzanie wartości i właściwości. Większość z tych funkcji została dodana w odpowiedzi na testy zgodności.

> [!NOTE]
> Należy dodać kilka funkcji walidacji dla dostawcy, aby przekazać OLE DB testy zgodności.

Ten dostawca wymaga dwóch procedur walidacji. Pierwsza procedura, `CRowsetImpl::ValidateCommandID`, jest częścią klasy zestawu wierszy. Jest on wywoływany podczas tworzenia zestawu wierszy przez szablony dostawców. Przykład korzysta z tej procedury, aby poinformować odbiorców, że nie obsługuje indeksów. Pierwsze wywołanie ma `CRowsetImpl::ValidateCommandID` (należy pamiętać, że Dostawca używa `_RowsetBaseClass` typedef dodanego w mapie interfejsu dla `CCustomRowset` w ramach [obsługi dostawców dla zakładek](../../data/oledb/provider-support-for-bookmarks.md), więc nie trzeba pisać tego długiego wiersza argumentów szablonu). Następnie Zwróć DB_E_NOINDEX, jeśli parametr index nie ma wartości NULL (oznacza to, że odbiorca chce użyć indeksu w Stanach Zjednoczonych). Aby uzyskać więcej informacji o identyfikatorach poleceń, zobacz specyfikację OLE DB i poszukaj `IOpenRowset::OpenRowset`.

Następujący kod jest `ValidateCommandID` procedury walidacji:

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

Szablony dostawcy wywołują metodę `OnPropertyChanged`, gdy ktoś zmieni właściwość w grupie DBPROPSET_ROWSET. Aby obsłużyć właściwości innych grup, należy dodać je do odpowiedniego obiektu (to jest, DBPROPSET_SESSION sprawdzenia w klasie `CCustomSession`).

Kod najpierw sprawdza, czy właściwość jest połączona z inną. Jeśli właściwość jest łańcucha, ustawia właściwość DBPROP_BOOKMARKS na `True`. Dodatek C specyfikacji OLE DB zawiera informacje na temat właściwości. Informacje te informują również o tym, czy właściwość jest łańcuchem do innej.

Możesz również dodać do kodu procedurę `IsValidValue`. Podczas próby ustawienia właściwości `IsValidValue` wywołanie szablonów. Tę metodę należy zastąpić, jeśli wymagane jest dodatkowe przetwarzanie podczas ustawiania wartości właściwości. Dla każdego zestawu właściwości można mieć jedną z tych metod.

## <a name="see-also"></a>Zobacz też

[Zaawansowane techniki dostawcy](../../data/oledb/advanced-provider-techniques.md)
