---
title: Testowanie dostawcy tylko do odczytu | Dokumentacja firmy Microsoft
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
- OLE DB providers, calling
- OLE DB providers, testing
ms.assetid: e4aa30c1-391b-41f8-ac73-5270e46fd712
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 4630391d9bce319c35af18767d7133bd34a92362
ms.sourcegitcommit: c045c3a7e9f2c7e3e0de5b7f9513e41d8b6d19b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2018
ms.locfileid: "49990207"
---
# <a name="testing-the-read-only-provider"></a>Testowanie dostawcy tylko do odczytu

Aby przetestować dostawcę, należy użytkownik. Pomaga ono, jeśli można dopasować użytkownika z dostawcą. Szablony konsumentów OLE DB są alokowania elastycznego otokę OLE DB i zgodne z obiektami COM dostawcy. Ponieważ źródłem jest dostarczany z szablonami konsumentów, jest łatwo debugować dostawcy z nimi. Szablony konsumentów są również bardzo małe i szybki sposób rozwijać aplikacje komercyjne.  
  
W przykładzie w tym temacie tworzy domyślną aplikację Kreator aplikacji MFC dla użytkownika testowego. Aplikacja testowa jest proste okno dialogowe z szablonu kod konsumenta OLE DB, dodane.  
  
## <a name="to-create-the-test-application"></a>Aby utworzyć aplikację testu  
  
1. Na **pliku** menu, kliknij przycisk **New**, a następnie kliknij przycisk **projektu**.  
  
1. W **typów projektów** okienku wybierz **projekty języka Visual C++** folderu. W **szablony** okienku wybierz **aplikacji MFC**.  
  
1. Wprowadź nazwę projektu *TestProv*, a następnie kliknij przycisk **OK**.  
  
     Zostanie wyświetlony Kreator aplikacji MFC.  
  
1. Na **typ aplikacji** wybierz opcję **oparte o okna dialogowe**.  
  
1. Na **funkcje zaawansowane** wybierz opcję **automatyzacji**, a następnie kliknij przycisk **Zakończ**.  
  
> [!NOTE]
> Aplikacja nie wymaga obsługi automatyzacji, jeśli dodasz `CoInitialize` w `CTestProvApp::InitInstance`.  
  
Można wyświetlać i edytować **TestProv** okno dialogowe (IDD_TESTPROV_DIALOG), wybierając je w **widok zasobów**. W oknie dialogowym, należy umieścić dwa pola listy, po jednym dla każdego ciągu w zestawie wierszy. Wyłączyć właściwość sortowania dla obu pola listy, naciskając klawisz **Alt**+**Enter** po wybraniu pola listy, klikając **style** kartę, a następnie usuwając zaznaczenie  **Sortuj** pole wyboru. Ponadto Umieść **Uruchom** przycisku na okno dialogowe, aby pobrać plik. Zakończono **TestProv** okno dialogowe powinna mieć dwa pola listy, odpowiednio oznaczone jako "W ciągu 1" i "2 ciąg"; ma on także **OK**, **anulować**, i **uruchamiania**  przycisków.  
  
Otwórz plik nagłówkowy klasy okien dialogowych (w tym TestProvDlg.h wielkości liter). Dodaj następujący kod do pliku nagłówka (poza wszelkimi deklaracjami klasy):  
  
```cpp
////////////////////////////////////////////////////////////////////////  
// TestProvDlg.h  
  
class CProvider   
{  
// Attributes  
public:  
   char   szField1[16];  
   char   szField2[16];  
  
   // Binding Maps  
BEGIN_COLUMN_MAP(CProvider)  
   COLUMN_ENTRY(1, szField1)  
   COLUMN_ENTRY(2, szField2)  
END_COLUMN_MAP()  
};  
```  
  
Kod reprezentuje rekord użytkownika, który definiuje kolumny będą w zestawie wierszy. Kiedy klient wywołuje `IAccessor::CreateAccessor`, aby określić kolumny, które można powiązać używa tych wpisów. Szablony konsumentów OLE DB pozwalają również na dynamiczne powiązanie kolumn. Makra COLUMN_ENTRY są makra PROVIDER_COLUMN_ENTRY w wersji po stronie klienta. Dwa makra COLUMN_ENTRY Określ numer i typ, długość oraz dane elementu członkowskiego dla dwóch ciągów.  
  
Dodawanie funkcji obsługi dla **Uruchom** przycisku, naciskając klawisz **Ctrl** i dwukrotne kliknięcie **Uruchom** przycisku. Umieść następujący kod w funkcji:  
  
```cpp
///////////////////////////////////////////////////////////////////////  
// TestProvDlg.cpp  
  
void CtestProvDlg::OnRun()  
{  
   CCommand<CAccessor<CProvider>> table;  
   CDataSource source;  
   CSession   session;  
  
   if (source.Open("MyProvider.MyProvider.1", NULL) != S_OK)  
      return;  
  
   if (session.Open(source) != S_OK)  
      return;  
  
   if (table.Open(session, _T("c:\\samples\\myprov\\myData.txt")) != S_OK)  
      return;  
  
   while (table.MoveNext() == S_OK)  
   {  
      m_ctlString1.AddString(table.szField1);  
      m_ctlString2.AddString(table.szField2);  
   }  
}  
```  
  
`CCommand`, `CDataSource`, I `CSession` klasy wszystkie należeć do szablony konsumentów OLE DB. Każda klasa naśladuje obiektów COM w dostawcy. `CCommand` Przyjmuje obiekt `CProvider` klasy, zadeklarowana w pliku nagłówkowym, jako parametr szablonu. `CProvider` Parametr reprezentuje powiązań, które umożliwiają dostęp do danych od dostawcy. Oto `Open` kod dla źródła danych, sesji i polecenia:  
  
```cpp  
if (source.Open("MyProvider.MyProvider.1", NULL) != S_OK)  
   return;  
  
if (session.Open(source) != S_OK)  
   return;  
  
if (table.Open(session, _T("c:\\samples\\myprov\\myData.txt")) != S_OK)  
   return;  
```  
  
Wiersze, które można otworzyć każdą z klas tworzenia każdego obiektu modelu COM w dostawcy. Aby zlokalizować dostawcę, należy użyć `ProgID` dostawcy. Możesz uzyskać `ProgID` z rejestru systemowego lub przez wyszukiwanie w pliku MyProvider.rgs (Otwórz katalog dostawcy i wyszukaj `ProgID` klucza).  
  
Plik MyData.txt jest dołączany `MyProv` próbki. Aby utworzyć plik samodzielnie, należy użyć edytora, a następnie wpisz parzystą liczbę ciągów, naciskając klawisz ENTER między każdego ciągu. Jeśli plik zostanie przeniesiony, należy zmienić nazwę ścieżki.  
  
Przekaż w ciągu "c:\\\samples\\\myprov\\\MyData.txt" w `table.Open` wiersza. Jeśli znajdujesz się w `Open` wywołanie, zobaczysz, że ten ciąg jest przekazywany do `SetCommandText` metody w dostawcy. Należy pamiętać, że `ICommandText::Execute` metody używane te parametry.  
  
Aby pobrać dane, należy wywołać `MoveNext` w tabeli. `MoveNext` wywołania `IRowset::GetNextRows`, `GetRowCount`, i `GetData` funkcji. Gdy nie ma żadnych więcej wierszy (bieżąca pozycja w zestawie wierszy jest większa niż `GetRowCount`), kończy się pętla:  
  
```cpp  
while (table.MoveNext() == S_OK)  
{  
   m_ctlString1.AddString(table.szField1);  
   m_ctlString2.AddString(table.szField2);  
}  
```  
  
Należy pamiętać, że w przypadku Brak kolejnych wierszy dostawców zwracają DB_S_ENDOFROWSET. Wartość DB_S_ENDOFROWSET nie jest błąd. Należy zawsze sprawdzić, względem S_OK, aby anulować pętli pobierania danych i używaj makro zakończone POWODZENIEM.  
  
Powinny teraz mieć możliwość tworzenia i testowania programu.  
  
## <a name="see-also"></a>Zobacz też  

[Udoskonalanie prostego dostawcy tylko do odczytu](../../data/oledb/enhancing-the-simple-read-only-provider.md)