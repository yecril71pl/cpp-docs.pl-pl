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
ms.openlocfilehash: 0e45e16b42505d34ea4340b991638405e7161eb5
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46030285"
---
# <a name="recordset-architecture-odbc"></a>Zestaw rekordów: architektura (ODBC)

Ten temat dotyczy klas MFC ODBC.  
  
W tym temacie opisano elementy członkowskie danych składające się z architekturą obiekty zestawów rekordów:  
  
- [Elementy członkowskie danych pola](#_core_field_data_members)  
  
- [Elementy członkowskie danych parametru](#_core_parameter_data_members)  
  
- [Za pomocą m_nfields — i m_nparams — elementy członkowskie danych](#_core_using_m_nfields_and_m_nparams)  
  
> [!NOTE]
>  Ten temat dotyczy obiektów pochodzących od `CRecordset` w wierszu zbiorczego, które podczas pobierania nie została zaimplementowana. Jeśli zaimplementowano zbiorcze pobieranie z wiersza architektura jest podobna. Aby poznać różnice, zobacz [zestaw rekordów: pobieranie rekordów w zbiorcze (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
##  <a name="_core_a_sample_class"></a> Przykładowa klasa  

Kiedy używać [Kreator użytkownika interfejsu ODBC MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md) z **Dodaj klasę** pochodną kreatora, aby zadeklarować klasy zestawu rekordów `CRecordset`, wynikowy klasa ma ogólną strukturę pokazano w następującym prosty klasa:  
  
```cpp  
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
  
Na początku klasy, kreator zapisuje zbiór [elementy członkowskie danych pola](#_core_field_data_members). Podczas tworzenia klasy należy określić co najmniej jednego członka danych pola. Jeśli klasa jest sparametryzowane, jako przykład klasy jest (z elementem członkowskim danych `m_strIDParam`), należy ręcznie dodać [elementy członkowskie danych parametru](#_core_parameter_data_members). Kreator nie obsługuje dodawania parametrów do klasy.  
  
##  <a name="_core_field_data_members"></a> Elementy członkowskie danych pola  

Najważniejsze elementy członkowskie klasy zestawu rekordów są elementy członkowskie danych pola. Dla każdej kolumny, którą wybierzesz ze źródła danych klasa zawiera element członkowski danych o typie danych odpowiednie dla tej kolumny. Na przykład [przykładowa klasa](#_core_a_sample_class) wyświetlane na początku tego tematu zawiera dwa elementy członkowskie pola, oba typu `CString`, co jest nazywane `m_strCourseID` i `m_strCourseTitle`.  
  
Gdy zestaw rekordów wybierze zestaw rekordów, struktura automatycznie wiąże kolumny bieżącego rekordu (po `Open` wywołanie, pierwszy rekord jest bieżąca) do elementów członkowskich danych pola obiektu. Oznacza to, że struktura używa odpowiednie pole składowej danych jako bufor do przechowywania zawartości kolumny rekordu.  
  
Jak użytkownik przewija widok nowy rekord, struktura używa elementy członkowskie danych pola, który reprezentuje bieżący rekord. Struktura odświeża elementy członkowskie danych pola, zastępując wartości poprzedniej rekordu. Elementy członkowskie danych pola są również używane do aktualizowania bieżącego rekordu i dodania nowych rekordów. W ramach procesu aktualizowania rekordu możesz określić wartości aktualizacji, przypisując wartości bezpośrednio do odpowiedniego pola element członkowski danych lub elementów członkowskich.  
  
##  <a name="_core_parameter_data_members"></a> Elementy członkowskie danych parametru  

Jeśli klasa jest sparametryzowane, ma co najmniej jednego członka danych parametru. Klasa sparametryzowana pozwala Ci zapytania rekordów na informacjach uzyskanych lub obliczane w czasie wykonywania.  
  
Zazwyczaj parametr umożliwia zawężenie zaznaczenia, jak w poniższym przykładzie. Na podstawie [przykładowa klasa](#_core_a_sample_class) na początku tego tematu, obiekty zestawów rekordów może wykonać następującą instrukcję SQL:  
  
```sql  
SELECT CourseID, CourseTitle FROM Course WHERE CourseID = ?  
```  
  
"?" Jest symbolem zastępczym dla wartości parametru, który podasz w czasie wykonywania. Podczas konstruowania zestawu rekordów i ustaw jego `m_strIDParam` staje się od instrukcji SQL zestawu rekordów element członkowski danych do MATH101,:  
  
```sql  
SELECT CourseID, CourseTitle FROM Course WHERE CourseID = MATH101  
```  
  
Definiując elementy członkowskie danych parametru, poinformować szablon o parametrach w parametrach SQL. Struktura wiąże parametr, który umożliwia ODBC, o których wiadomo, gdzie można uzyskać wartości do zastąpienia symboli zastępczych. W tym przykładzie Wynikowy zestaw rekordów zawiera tylko rekord z tabeli Kurs z kolumną CourseID, którego wartością jest MATH101. Wybrano wszystkie określone kolumny tego rekordu. Można określić dowolną liczbę parametrów (i symbole zastępcze) według potrzeb.  
  
> [!NOTE]
>  MFC nie robi nic, samego, przy użyciu parametrów — w szczególności, ale nie wykonuje podstawianie tekstu. Zamiast tego MFC informuje ODBC do uzyskania parameter; ODBC pobiera dane i wykonuje niezbędne parametryzacji.  
  
> [!NOTE]
>  Ważna jest kolejność parametrów. Uzyskać informacje na ten temat i więcej informacji na temat parametrów, zobacz [zestaw rekordów: parametryzacja zestawu rekordów (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).  
  
##  <a name="_core_using_m_nfields_and_m_nparams"></a> Przy użyciu m_nfields — i m_nparams —  

Gdy kreator zapisuje konstruktora dla klasy, również inicjuje [m_nfields —](../../mfc/reference/crecordset-class.md#m_nfields) element członkowski danych, która określa liczbę [elementy członkowskie danych pola](#_core_field_data_members) w klasie. Jeśli dodasz dowolne [parametry](#_core_parameter_data_members) do klasy, musisz również dodać inicjowanie [m_nparams —](../../mfc/reference/crecordset-class.md#m_nparams) element członkowski danych, która określa liczbę elementy członkowskie danych parametru. Struktura używa tych wartości do pracy z elementów członkowskich danych.  
  
Aby uzyskać więcej informacji i przykładów, zobacz [wymiana pól rekordów: za pomocą RFX](../../data/odbc/record-field-exchange-using-rfx.md).  
  
## <a name="see-also"></a>Zobacz też  

[Zestaw rekordów (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Zestaw rekordów: deklarowanie klasy dla tabeli (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md)<br/>
[Wymiana pól rekordów (RFX)](../../data/odbc/record-field-exchange-rfx.md)