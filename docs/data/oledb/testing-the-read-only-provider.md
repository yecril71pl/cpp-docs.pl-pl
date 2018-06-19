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
ms.openlocfilehash: 703d33f44fae534b206050e85086edb1ccc816f9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33112683"
---
# <a name="testing-the-read-only-provider"></a>Testowanie dostawcy tylko do odczytu
Aby przetestować dostawcę, należy konsumenta. Pomaga, jeśli użytkownika można dopasować do dostawcy. Szablony konsumentów OLE DB są cienką otoką wokół OLE DB i zgodne z obiektami COM dostawcy. Ponieważ źródłem jest dostarczany z szablonami konsumentów, jest łatwe debugowanie dostawcy z nimi. Szablony konsumentów są również bardzo mała i szybkie sposób tworzenia aplikacji klienta.  
  
 W tym temacie tworzona domyślnej aplikacji Kreator aplikacji MFC dla użytkownika testowego. Aplikacja testowa jest proste okna dialogowego z kodem szablon konsumenta OLE DB dodane.  
  
### <a name="to-create-the-test-application"></a>Aby utworzyć aplikację testu  
  
1.  Na **pliku** menu, kliknij przycisk **nowy**, a następnie kliknij przycisk **projektu**.  
  
2.  Wybierz w okienku typów projektów **projekty Visual C++** folderu. W okienku szablonów wybierz **aplikacji MFC**.  
  
3.  Wprowadź nazwę projektu **TestProv**, a następnie kliknij przycisk **OK**.  
  
     Zostanie wyświetlony Kreator aplikacji MFC.  
  
4.  Na **typu aplikacji** wybierz pozycję **okno dialogowe na podstawie**.  
  
5.  Na **funkcje zaawansowane** wybierz pozycję **automatyzacji**, a następnie kliknij przycisk **Zakończ**.  
  
> [!NOTE]
>  Aplikacja nie wymaga Obsługa automatyzacji, jeśli dodasz **CoInitialize** w **CTestProvApp::InitInstance**.  
  
 Możesz wyświetlić i edytować okno dialogowe TestProv (IDD_TESTPROV_DIALOG), wybierz je w widoku zasobów. Umieść dwa pola listy, po jednej dla każdego ciągu w zestawie wierszy w oknie dialogowym. Wyłącz właściwości sortowania dla obu pola listy, naciskając klawisze ALT + Enter gdy zaznaczone jest pole listy, klikając **style** , a następnie wyczyszczenie **sortowania** pole wyboru. Również umieścić **Uruchom** przycisk w oknie dialogowym, aby pobrać plik. Okno dialogowe zakończono TestProv powinien mieć dwa pola listy z etykietą "W ciągu 1" i "W ciągu 2", odpowiednio; obejmuje ona również **OK**, **anulować**, i **Uruchom** przycisków.  
  
 Otwórz plik nagłówka klasy okien dialogowych (w tym TestProvDlg.h przypadków). Dodaj następujący kod do pliku nagłówka (poza wszelkimi deklaracjami klasy):  
  
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
  
 Kod reprezentuje rekord użytkownika, który definiuje, jakie będą kolumn w zestawie wierszy. Kiedy klient wywołuje **IAccessor::CreateAccessor**, używa te wpisy, aby określić, które kolumny do powiązania. Szablony konsumentów OLE DB pozwalają również na dynamiczne powiązanie kolumn. Column_entry — makra są makra PROVIDER_COLUMN_ENTRY wersję klienta. Dwa makra column_entry — Określ numer, członka typu, długość i danych dla dwóch ciągów.  
  
 Dodanie funkcji programu obsługi dla **Uruchom** przycisku, naciskając klawisz CTRL i klikając dwukrotnie **Uruchom** przycisku. Umieść następujący kod w funkcji:  
  
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
  
 `CCommand`, `CDataSource`, I `CSession` klasy wszystkie należą do szablony konsumentów OLE DB. Każda klasa naśladuje obiektów COM w dostawcy. `CCommand` Obiekt ma `CProvider` klasy, zadeklarowanej w pliku nagłówka, jako parametr szablonu. `CProvider` Parametr reprezentuje powiązań, które umożliwiają dostęp do danych od dostawcy. Oto `Open` kodu dla źródła danych, sesji i polecenia:  
  
```  
if (source.Open("MyProvider.MyProvider.1", NULL) != S_OK)  
   return;  
  
if (session.Open(source) != S_OK)  
   return;  
  
if (table.Open(session, _T("c:\\samples\\myprov\\myData.txt")) != S_OK)  
   return;  
```  
  
 Wiersze, aby otworzyć klas tworzenie każdego obiektu modelu COM w dostawcy. Aby zlokalizować dostawcy, użyj identyfikatora ProgID dostawcy. Identyfikator ProgID można uzyskać z rejestru systemowego lub przez przeszukiwanie w pliku MyProvider.rgs (Otwórz katalog i wyszukaj klucz ProgID dostawcy).  
  
 Plik MyData.txt znajduje się przykład MyProv. Aby utworzyć własny plik, użyj edytora i wpisz parzysta liczba ciągów, naciskając klawisz ENTER między każdym ciągu. Zmień nazwę ścieżki, jeśli plik zostanie przeniesiony.  
  
 Podaj ciąg "c:\\\samples\\\myprov\\\MyData.txt" w `table.Open` wiersza. Jeśli krok do `Open` wywołanie, zostanie wyświetlony że ten ciąg jest przekazywany do `SetCommandText` metody w dostawcy. Należy pamiętać, że `ICommandText::Execute` metody użyć tego ciągu.  
  
 Aby pobrać dane, należy wywołać `MoveNext` w tabeli. `MoveNext` wywołania **IRowset::GetNextRows**, `GetRowCount`, i `GetData` funkcji. Jeśli nie ma żadnych więcej wierszy (bieżącą pozycję w zestawie wierszy jest większa niż `GetRowCount`), kończy Pętla:  
  
```  
while (table.MoveNext() == S_OK)  
{  
   m_ctlString1.AddString(table.szField1);  
   m_ctlString2.AddString(table.szField2);  
}  
```  
  
 Należy pamiętać, że jeśli nie ma żadnych więcej wierszy, zwracać dostawców **DB_S_ENDOFROWSET**. **DB_S_ENDOFROWSET** wartość nie jest błąd. Należy zawsze sprawdzić przed `S_OK` Aby anulować pętli pobierania danych i nie używać makro zakończyło się pomyślnie.  
  
 Teraz można umożliwiający zbudowanie i przetestowanie program.  
  
## <a name="see-also"></a>Zobacz też  
 [Udoskonalanie prostego dostawcy tylko do odczytu](../../data/oledb/enhancing-the-simple-read-only-provider.md)