---
title: 'Zestaw rekordów: Architektura (ODBC) | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- recordsets, data members
- field data members, recordset architecture
- field data members
- m_nParams data member, recordsets
- recordsets, architecture
- parameter data members in recordsets
- m_nFields data member
- ODBC recordsets, architecture
- m_nParams data member
- m_nFields data member, recordsets
ms.assetid: 47555ddb-11be-4b9e-9b9a-f2931764d298
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 5be3ec16ec01a6c6db2e24b1b6a6260f3a44bfec
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33092213"
---
# <a name="recordset-architecture-odbc"></a>Zestaw rekordów: architektura (ODBC)
Ten temat dotyczy klasach MFC ODBC.  
  
 W tym temacie opisano elementy członkowskie danych, wchodzące w skład architektura obiektu zestaw rekordów:  
  
-   [Elementy członkowskie danych pola](#_core_field_data_members)  
  
-   [Elementy członkowskie danych parametru](#_core_parameter_data_members)  
  
-   [Przy użyciu m_nfields — i m_nparams — elementy członkowskie danych](#_core_using_m_nfields_and_m_nparams)  
  
> [!NOTE]
>  Ten temat dotyczy obiektów pochodzących od `CRecordset` w wiersz, który zbiorczego pobierania nie została zaimplementowana. Jeśli zaimplementowano zbiorcze pobieranie z wiersza przypomina architektury. Aby poznać różnice, zobacz [zestaw rekordów: pobieranie rekordów zbiorczego (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
##  <a name="_core_a_sample_class"></a> Przykładowe klasy  
 Jeśli używasz [Kreator konsumenta MFC ODBC](../../mfc/reference/adding-an-mfc-odbc-consumer.md) z **Dodaj klasę** kreatora, aby zadeklarować klasy rekordów pochodzące z `CRecordset`, wynikowy klasa ma ogólną strukturę pokazano poniżej proste klasy:  
  
```  
class CCourse : public CRecordset  
{  
public:  
   CCourse(CDatabase* pDatabase = NULL);  
   ...  
   CString m_strCourseID;  
   CString m_strCourseTitle;  
   CString m_strIDParam;  
};  
```  
  
 Na początku tej klasy, kreator zapisuje zbiór [elementy członkowskie danych pola](#_core_field_data_members). Podczas tworzenia klasy należy określić co najmniej jednego członka danych pola. Jeśli klasa jest sparametryzowana, jako przykład klasy jest (z elementem członkowskim danych `m_strIDParam`), musisz ręcznie dodać [elementy członkowskie danych parametru](#_core_parameter_data_members). Kreator nie obsługuje dodawania parametrów do klasy.  
  
##  <a name="_core_field_data_members"></a> Elementy członkowskie danych pola  
 Najważniejsze elementy członkowskie klasy rekordów są elementy członkowskie danych pola. Dla każdej kolumny, którą wybierzesz ze źródła danych klasa zawiera element członkowski danych klasy odpowiedni typ danych dla tej kolumny. Na przykład [przykładowe klasy](#_core_a_sample_class) wyświetlane na początku tego tematu zawiera dwa elementy członkowskie danych pola, zarówno typu `CString`o nazwie `m_strCourseID` i `m_strCourseTitle`.  
  
 Gdy zestaw rekordów wybierze zestawu rekordów, platformę automatycznie wiąże kolumn bieżącego rekordu (po **Otwórz** wywołanie, pierwszy rekord jest bieżący) do elementy członkowskie danych pola obiektu. Oznacza to platformę używa elementu członkowskiego danych odpowiednie pole jako bufor do przechowywania zawartości kolumny rekordu.  
  
 Użytkownik przewija widok do nowego rekordu, struktury elementy członkowskie danych pola do reprezentowania używany dla bieżącego rekordu. Platformę odświeża elementy członkowskie danych pola, zastępując wartości poprzedniego rekordu. Elementy członkowskie danych pola są również używane do aktualizowania bieżącego rekordu i dodania nowych rekordów. W ramach procesu aktualizacji rekordu możesz określić wartości aktualizacji przez przypisanie wartości bezpośrednio do elementu członkowskiego danych w odpowiednim polu lub elementy członkowskie.  
  
##  <a name="_core_parameter_data_members"></a> Elementy członkowskie danych parametru  
 Jeśli klasa jest sparametryzowana, ma co najmniej jednego członka danych parametru. Klasa sparametryzowana pozwala Ci zapytania rekordów na informacjach uzyskanych lub obliczane w czasie wykonywania.  
  
 Zazwyczaj parametr umożliwia zawężenie zaznaczenia, jak w poniższym przykładzie. Na podstawie [przykładowe klasy](#_core_a_sample_class) na początku tego tematu, obiekt zestawu rekordów może wykonać następującą instrukcję SQL:  
  
```  
SELECT CourseID, CourseTitle FROM Course WHERE CourseID = ?  
```  
  
 "?" To symbol zastępczy wartości parametru, wprowadzona w czasie wykonywania. Podczas tworzenia zestawu rekordów i ustawić jej `m_strIDParam` element członkowski danych do MATH101, skutecznego instrukcji SQL zestawu rekordów staje się:  
  
```  
SELECT CourseID, CourseTitle FROM Course WHERE CourseID = MATH101  
```  
  
 Definiując elementy członkowskie danych parametru platformę Opisz parametrów w ciągu SQL. Platformę wiąże parametr, który umożliwia ODBC wiedzieć, gdzie można uzyskać wartości do zastąpienia symboli zastępczych. W tym przykładzie Wynikowy zestaw rekordów zawiera rekord z tabeli kursu z kolumną CourseID, którego wartość jest MATH101. Wybrano wszystkich określonych kolumn tego rekordu. Można określić dowolną liczbę parametrów (i symbole zastępcze) zgodnie z potrzebami.  
  
> [!NOTE]
>  MFC nie robi nic się z parametrami — w szczególności nie wykonuje podstawienie tekstu. Zamiast tego MFC informuje ODBC do uzyskania parametru; ODBC pobiera dane i wykonuje niezbędne parametry.  
  
> [!NOTE]
>  Ważna jest kolejność parametrów. Informacje na ten temat i więcej informacji na temat parametrów, zobacz [zestaw rekordów: parametryzacja zestawu rekordów (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).  
  
##  <a name="_core_using_m_nfields_and_m_nparams"></a> Przy użyciu m_nfields — i m_nparams —  

 Gdy kreator zapisuje konstruktora dla klasy, inicjuje również [m_nfields —](../../mfc/reference/crecordset-class.md#m_nfields) danych elementu członkowskiego, który określa liczbę [elementy członkowskie danych pola](#_core_field_data_members) w klasie. Jeśli dodasz dowolne [parametry](#_core_parameter_data_members) do klasy, musisz również dodać inicjowania dla [m_nparams —](../../mfc/reference/crecordset-class.md#m_nparams) danych elementu członkowskiego, który określa liczbę elementy członkowskie danych parametru. Platforma korzysta z tych wartości do pracy z elementami członkowskimi danych.  
  
 Aby uzyskać dodatkowe informacje i przykłady, zobacz [wymiana pól rekordów: za pomocą RFX](../../data/odbc/record-field-exchange-using-rfx.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Zestaw rekordów (ODBC)](../../data/odbc/recordset-odbc.md)   
 [Zestaw rekordów: Deklarowanie klasy dla tabeli (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md)   
 [Wymiana pól rekordów (RFX)](../../data/odbc/record-field-exchange-rfx.md)