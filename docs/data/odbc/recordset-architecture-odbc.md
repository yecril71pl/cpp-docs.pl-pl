---
title: 'Zestaw rekordów: architektura (ODBC)'
ms.date: 11/04/2016
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
ms.openlocfilehash: bb4b67a4c534598a8e26eb9ab5f297b108b67b6d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212995"
---
# <a name="recordset-architecture-odbc"></a>Zestaw rekordów: architektura (ODBC)

Ten temat dotyczy klas MFC ODBC.

W tym temacie opisano składowe danych, które składają się na architekturę obiektu zestawu rekordów:

- [Elementy członkowskie danych pola](#_core_field_data_members)

- [Elementy członkowskie danych parametru](#_core_parameter_data_members)

- [Używanie m_nFields i m_nParams składowych danych](#_core_using_m_nfields_and_m_nparams)

> [!NOTE]
>  Ten temat dotyczy obiektów pochodnych `CRecordset`, w których nie zaimplementowano pobierania wierszy zbiorczych. W przypadku zaimplementowania pobierania wierszy zbiorczych architektura jest podobna. Aby zrozumieć różnice, zobacz [zestaw rekordów: pobieranie rekordów zbiorczo (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

##  <a name="sample-class"></a><a name="_core_a_sample_class"></a>Klasa Przykładowa

> [!NOTE]
> Kreator użytkownika ODBC MFC nie jest dostępny w programie Visual Studio 2019 i nowszych. Nadal można utworzyć konsumenta ręcznie.

W przypadku używania [Kreatora interfejsu użytkownika ODBC MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md) z kreatora **dodawania klasy** do deklarowania klasy zestawu rekordów pochodnej od `CRecordset`, wynikowa Klasa ma strukturę ogólną pokazaną w następującej prostej klasie:

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

Na początku klasy kreator zapisuje zestaw [elementów członkowskich danych](#_core_field_data_members). Podczas tworzenia klasy należy określić co najmniej jeden element członkowski danych pola. Jeśli klasa jest sparametryzowane, ponieważ Klasa Przykładowa jest (z elementem członkowskim danych `m_strIDParam`), należy ręcznie dodać [elementy członkowskie danych parametru](#_core_parameter_data_members). Kreator nie obsługuje dodawania parametrów do klasy.

##  <a name="field-data-members"></a><a name="_core_field_data_members"></a>Elementy członkowskie danych pola

Najważniejszymi elementami członkowskimi klasy zestawu rekordów są elementy danych pola. Dla każdej zaznaczonej kolumny ze źródła danych Klasa zawiera element członkowski danych o odpowiednim typie danych dla tej kolumny. Przykładowo [Klasa Przykładowa](#_core_a_sample_class) pokazana na początku tego tematu ma dwa elementy członkowskie danych pól, obu typów `CString`, nazywane `m_strCourseID` i `m_strCourseTitle`.

Gdy zestaw rekordów wybiera zestaw rekordów, struktura automatycznie wiąże kolumny bieżącego rekordu (po wywołaniu `Open`, pierwszy rekord jest bieżący) do elementów członkowskich danych tego obiektu. Oznacza to, że struktura używa odpowiedniego elementu członkowskiego danych pola jako buforu do przechowywania zawartości kolumny rekordu.

Gdy użytkownik przewija nowy rekord, struktura używa elementów członkowskich danych pola do reprezentowania bieżącego rekordu. Struktura odświeża elementy członkowskie danych pola, zastępując wartości poprzedniego rekordu. Elementy członkowskie danych pola są również używane do aktualizowania bieżącego rekordu i dodawania nowych rekordów. W ramach procesu aktualizowania rekordu należy określić wartości aktualizacji, przypisując wartości bezpośrednio do odpowiedniego elementu członkowskiego danych pola lub członków.

##  <a name="parameter-data-members"></a><a name="_core_parameter_data_members"></a>Elementy członkowskie danych parametru

Jeśli klasa jest sparametryzowane, zawiera co najmniej jeden element członkowski danych parametru. Klasa sparametryzowanej umożliwia oparcie zapytania zestawu rekordów o informacjach uzyskanych lub obliczonych w czasie wykonywania.

Zazwyczaj parametr pozwala zawęzić wybór, jak w poniższym przykładzie. Na podstawie [przykładowej klasy](#_core_a_sample_class) na początku tego tematu obiekt Recordset może wykonać następującą instrukcję SQL:

```sql
SELECT CourseID, CourseTitle FROM Course WHERE CourseID = ?
```

"?" Jest symbolem zastępczym dla wartości parametru, która jest dostarczana w czasie wykonywania. Podczas konstruowania zestawu rekordów i ustawiania jego składowej danych `m_strIDParam` MATH101, obowiązująca instrukcja SQL dla zestawu rekordów przyjmuje następujące wartości:

```sql
SELECT CourseID, CourseTitle FROM Course WHERE CourseID = MATH101
```

Definiując elementy członkowskie danych parametrów, poinformujemy platformę o parametrach w ciągu SQL. Struktura wiąże parametr, który umożliwia ODBC, gdzie należy uzyskać wartości, aby zastąpić symbol zastępczy. W przykładzie powstały zestaw rekordów zawiera tylko rekord z tabeli kursów z kolumną CourseID, której wartością jest MATH101. Wybrano wszystkie określone kolumny tego rekordu. Możesz określić tyle parametrów (i symboli zastępczych), ile potrzebujesz.

> [!NOTE]
>  MFC nie robi nic w sobie z parametrami — w szczególności nie wykonuje podstawienia tekstu. Zamiast tego, MFC instruuje ODBC, gdzie pobrać parametr; ODBC pobiera dane i wykonuje niezbędne parametryzacja.

> [!NOTE]
>  Kolejność parametrów jest ważna. Aby uzyskać informacje na temat tego i więcej informacji o parametrach, zobacz [zestaw rekordów: parametryzacja a zestaw rekordów (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).

##  <a name="using-m_nfields-and-m_nparams"></a><a name="_core_using_m_nfields_and_m_nparams"></a>Używanie m_nFields i m_nParams

Gdy kreator zapisuje konstruktora dla klasy, inicjuje również element członkowski danych [m_nFields](../../mfc/reference/crecordset-class.md#m_nfields) , który określa liczbę [elementów członkowskich danych pola](#_core_field_data_members) w klasie. W przypadku dodania dowolnych [parametrów](#_core_parameter_data_members) do klasy należy również dodać inicjalizację dla elementu członkowskiego danych [m_nParams](../../mfc/reference/crecordset-class.md#m_nparams) , który określa liczbę elementów członkowskich danych parametru. Struktura używa tych wartości do pracy z elementami członkowskimi danych.

Aby uzyskać więcej informacji i przykładów, zobacz temat [wymiana pól rekordów: używanie RFX](../../data/odbc/record-field-exchange-using-rfx.md).

## <a name="see-also"></a>Zobacz też

[Zestaw rekordów (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Zestaw rekordów: deklarowanie klasy dla tabeli (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md)<br/>
[Wymiana pól rekordów (RFX)](../../data/odbc/record-field-exchange-rfx.md)
