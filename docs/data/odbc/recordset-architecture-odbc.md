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
ms.openlocfilehash: 3ed6a862cda769769cd07d2dcd72007292068dc3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367098"
---
# <a name="recordset-architecture-odbc"></a>Zestaw rekordów: architektura (ODBC)

Ten temat dotyczy klas MFC ODBC.

W tym temacie opisano elementy członkowskie danych, które składają się na architekturę obiektu zestaw rekordów:

- [Elementy członkowskie danych pól](#_core_field_data_members)

- [Elementy członkowskie danych parametrów](#_core_parameter_data_members)

- [Korzystanie z m_nFields i m_nParams elementów członkowskich danych](#_core_using_m_nfields_and_m_nparams)

> [!NOTE]
> Ten temat dotyczy obiektów pochodzących z `CRecordset` których pobieranie wiersza zbiorczego nie zostało zaimplementowane. Jeśli pobieranie wiersza zbiorczego jest implementowane, architektura jest podobna. Aby zrozumieć różnice, zobacz [Recordset: Pobieranie rekordów zbiorczo (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

## <a name="sample-class"></a><a name="_core_a_sample_class"></a>Klasa próbki

> [!NOTE]
> Kreator konsumenta odbc MFC nie jest dostępny w programie Visual Studio 2019 i nowszych. Nadal można utworzyć konsumenta ręcznie.

Podczas korzystania z [Kreatora konsumenta MFC ODBC](../../mfc/reference/adding-an-mfc-odbc-consumer.md) z **Kreatora dodawania klasy** do deklarowania klasy zestaw rekordów `CRecordset`pochodną, wynikowa klasa ma ogólną strukturę pokazaną w następującej klasie prostej:

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

Na początku klasy kreator zapisuje zestaw elementów [członkowskich danych pola](#_core_field_data_members). Podczas tworzenia klasy należy określić jeden lub więcej elementów członkowskich danych pola. Jeśli klasa jest sparametryzowana, ponieważ klasa `m_strIDParam`przykładowa jest (z elementem członkowskim danych), należy ręcznie dodać [elementy członkowskie danych parametrów](#_core_parameter_data_members). Kreator nie obsługuje dodawania parametrów do klasy.

## <a name="field-data-members"></a><a name="_core_field_data_members"></a>Elementy członkowskie danych pól

Najważniejszymi członkami klasy zestaw rekordów są elementy członkowskie danych pola. Dla każdej kolumny wybranej ze źródła danych klasa zawiera element członkowski danych odpowiedniego typu danych dla tej kolumny. Na przykład [klasa przykładu](#_core_a_sample_class) pokazana na początku tego tematu ma `CString`dwa `m_strCourseID` `m_strCourseTitle`elementy członkowskie danych pola, oba typu , wywoływane i .

Gdy zestaw rekordów wybierze zestaw rekordów, struktura automatycznie wiąże kolumny bieżącego `Open` rekordu (po wywołaniu pierwszy rekord jest bieżący) z elementami elementów członkowskich danych pola obiektu. Oznacza to, że struktura używa odpowiedniego elementu członkowskiego danych pola jako buforu, w którym do przechowywania zawartości kolumny rekordu.

Gdy użytkownik przewija do nowego rekordu, struktura używa elementów członkowskich danych pola do reprezentowania bieżącego rekordu. Struktura odświeża elementy członkowskie danych pola, zastępując wartości poprzedniego rekordu. Elementy członkowskie danych pól są również używane do aktualizowania bieżącego rekordu i dodawania nowych rekordów. W ramach procesu aktualizowania rekordu można określić wartości aktualizacji, przypisując wartości bezpośrednio do odpowiedniego elementu członkowskiego lub elementów członkowskich danych pola.

## <a name="parameter-data-members"></a><a name="_core_parameter_data_members"></a>Elementy członkowskie danych parametrów

Jeśli klasa jest sparametryzowana, ma jeden lub więcej elementów członkowskich danych parametru. Klasa sparametryzowana umożliwia oparcie kwerendy na podstawie informacji uzyskanych lub obliczonych w czasie wykonywania.

Zazwyczaj parametr pomaga zawęzić zaznaczenie, jak w poniższym przykładzie. Na podstawie [klasy próbki](#_core_a_sample_class) na początku tego tematu obiekt zestaw rekordów może wykonać następującą instrukcję SQL:

```sql
SELECT CourseID, CourseTitle FROM Course WHERE CourseID = ?
```

"?" jest symbolem zastępczym dla wartości parametru, który można podać w czasie wykonywania. Podczas konstruowania zestawu rekordów i ustawić jego `m_strIDParam` element członkowski danych na MATH101, skuteczne instrukcji SQL dla zestawu rekordów staje się:

```sql
SELECT CourseID, CourseTitle FROM Course WHERE CourseID = MATH101
```

Definiując elementy członkowskie danych parametrów, można powiedzieć framework o parametrach w ciągu SQL. Struktura wiąże parametr, który pozwala ODBC wiedzieć, gdzie można uzyskać wartości zastąpić symbol zastępczy. W tym przykładzie wynikowy zestaw rekordów zawiera tylko rekord z tabeli Course z kolumną CourseID, której wartością jest MATH101. Zostaną wybrane wszystkie określone kolumny tego rekordu. Można określić dowolną liczbę parametrów (i symboli zastępczych).

> [!NOTE]
> MFC nie robi nic sam z parametrami — w szczególności nie wykonuje podstawiania tekstu. Zamiast tego MFC informuje ODBC, gdzie można uzyskać parametr; ODBC pobiera dane i wykonuje niezbędne parametryzację.

> [!NOTE]
> Kolejność parametrów jest ważna. Aby uzyskać informacje na ten temat i więcej informacji o parametrach, zobacz [Recordset: Parametrizing a Recordset (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).

## <a name="using-m_nfields-and-m_nparams"></a><a name="_core_using_m_nfields_and_m_nparams"></a>Korzystanie z m_nFields i m_nParams

Gdy kreator zapisuje konstruktora dla klasy, inicjuje również element członkowski [m_nFields](../../mfc/reference/crecordset-class.md#m_nfields) danych, który określa liczbę [elementów członkowskich danych pola](#_core_field_data_members) w klasie. Jeśli dodasz żadnych [parametrów](#_core_parameter_data_members) do klasy, należy również dodać inicjowanie dla [m_nParams](../../mfc/reference/crecordset-class.md#m_nparams) elementu członkowskiego danych, który określa liczbę elementów członkowskich danych parametrów. Struktura używa tych wartości do pracy z członkami danych.

Aby uzyskać więcej informacji i przykładów, zobacz [Wymiana pól rekordu: korzystanie z RFX](../../data/odbc/record-field-exchange-using-rfx.md).

## <a name="see-also"></a>Zobacz też

[Zestaw rekordów (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Zestaw rekordów: deklarowanie klasy dla tabeli (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md)<br/>
[Wymiana pól rekordu (RFX)](../../data/odbc/record-field-exchange-rfx.md)
