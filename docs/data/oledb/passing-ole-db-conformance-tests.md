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
ms.openlocfilehash: 11677e6295956de768c7ebc0c113d775b066bb0c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="passing-ole-db-conformance-tests"></a>Przechodzenie testów zgodności z OLE DB
Aby dostawców był bardziej spójny, zestaw SDK dostępu do danych zawiera zestaw testów zgodności z OLE DB. Testy Sprawdź wszystkie aspekty dostawcy i zapewniają wystarczającą pewność, że dostawca funkcji jako oczekiwano. Na temat zestawu SDK dostępu do danych firmy Microsoft można znaleźć testów zgodności z OLE DB. Tej części przedstawiono czynności, które należy wykonać przejść testy zgodności. Aby uzyskać informacje na temat uruchamiania testów zgodności z OLE DB zobacz zestaw SDK.  
  
## <a name="running-the-conformance-tests"></a>Uruchamianie testów zgodności  
 W programie Visual C++ 6.0 szablony dostawców OLE DB dodano szereg funkcji Przechwytywanie umożliwiają sprawdzanie właściwości i wartości. Większość tych funkcji dodanych w odpowiedzi na testów zgodności.  
  
> [!NOTE]
>  Należy dodać kilka funkcji sprawdzania poprawności dla dostawcy przekazać testów zgodności z OLE DB.  
  
 Ten dostawca wymaga dwóch procedur weryfikacji. Pierwszy rutynowych `CRowsetImpl::ValidateCommandID`, jest częścią klasy zestawu wierszy. Wywoływana podczas tworzenia zestawu wierszy za pomocą szablonów dostawcy. Przykład używa tej procedury do Poinformuj użytkowników, że nie obsługuje indeksów. Pierwsze wywołanie ma `CRowsetImpl::ValidateCommandID` (należy pamiętać, że dostawca używa **_RowsetBaseClass** typedef dodany do mapy interfejsu dla `CMyProviderRowset` w [Obsługa dostawców dla zakładek](../../data/oledb/provider-support-for-bookmarks.md), więc nie trzeba Typ tego wiersza dużo argumentów szablonu). Następnie należy zwrócić **DB_E_NOINDEX** Jeśli parametr indeksu nie jest **NULL** (oznacza to użytkownik chce używać indeksu na us). Aby uzyskać więcej informacji na temat identyfikatorów poleceń, zobacz specyfikację OLE DB i poszukaj **IOpenRowset::OpenRowset**.  
  
 Następujący kod jest **ValidateCommandID** procedury sprawdzania poprawności:  
  
```cpp
/////////////////////////////////////////////////////////////////////  
// MyProviderRS.H  
// Class: CMyProviderRowset   
  
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
  
 Wywołanie szablony dostawcy `OnPropertyChanged` metody zawsze, gdy użytkownik wprowadza zmiany właściwości na **DBPROPSET_ROWSET** grupy. Jeśli chcesz obsługiwać właściwości dla innych grup, należy je dodać do odpowiedniego obiektu (to znaczy **DBPROPSET_SESSION** kontroli go w programie `CMyProviderSession` klasy).  
  
 Kod najpierw sprawdza, czy właściwość jest połączone z innym. Jeśli właściwość jest powiązane, ustawia **DBPROP_BOOKMARKS** właściwości na wartość True. Dodatek C ze specyfikacją OLE DB zawiera informacje dotyczące właściwości. Te informacje również informuje, czy właściwość jest powiązany łańcuchem zależności z innym.  
  
 Można także dodać `IsValidValue` rutynowych w kodzie. Wywołanie szablony `IsValidValue` podczas próby ustawienia właściwości. Czy przesłonić tę metodę, jeśli potrzebujesz dodatkowego przetwarzania podczas ustawiania wartości właściwości. Może mieć jedną z następujących metod dla każdego zestawu właściwości.  
  
## <a name="threading-issues"></a>Problemy wielowątkowości  
 Domyślnie OLE DB Provider kreatora ATL OLE DB Provider kreatora generuje kod dla dostawcy do uruchamiania w modelu typu apartment. Jeśli użytkownik spróbuje uruchomić ten kod z testów zgodności, otrzymasz początkowo błędów. To jest ponieważ Ltm.exe, narzędzie używane do uruchamiania testów zgodności z OLE DB, domyślnie przyjmowana jest zwolnienia wątków. Wartość domyślna kodu OLE DB Provider kreatora z modelem typu apartment wydajności i łatwość użycia.  
  
 Aby rozwiązać ten problem, można zmienić LTM lub zmienić dostawcę.  
  
#### <a name="to-change-ltm-to-run-in-apartment-threaded-mode"></a>Aby zmienić LTM do uruchamiania w apartamencie wątku trybu  
  
1.  W menu głównym LTM kliknij **narzędzia**, a następnie kliknij przycisk **opcje**.  
  
2.  Na **ogólne** Zmień model wątkowy z **wolnych wątków** do **wątki w apartamencie**.  
  
 Aby zmienić dostawcą, aby uruchomić trybu wolnych wątków:  
  
-   W projekcie dostawcy wyszukiwania dla wszystkich wystąpień `CComSingleThreadModel` i zastąp go z `CComMultiThreadModel`, która powinna być w nagłówkach źródła, sesji i zestawu wierszy danych.  
  
-   W pliku .rgs zmienić model wątkowy z **apartamentu** do **zarówno**.  
  
-   Programowanie poprawne wykonaj zasady programowania bezpłatnie wątków (to znaczy blokadę zapisu).  
  
## <a name="see-also"></a>Zobacz też  
 [Zaawansowane techniki dostawcy](../../data/oledb/advanced-provider-techniques.md)