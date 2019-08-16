---
title: Kwestie projektowania architektonicznego OLE DB
ms.date: 05/09/2019
helpviewer_keywords:
- OLE DB, application design considerations
ms.assetid: 8caa7d99-d2bb-42c9-8884-74f228bb6ecc
ms.openlocfilehash: b481d9948d3055247bd284ca794a0fa65905e21b
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69501346"
---
# <a name="ole-db-architectural-design-issues"></a>Kwestie projektowania architektonicznego OLE DB

> [!NOTE]
> Kreator użytkownika ATL OLE DB nie jest dostępny w programie Visual Studio 2019 i nowszych. Można nadal ręcznie dodawać funkcje. Aby uzyskać więcej informacji, zobacz [Tworzenie klienta bez korzystania z Kreatora](creating-a-consumer-without-using-a-wizard.md).

Przed uruchomieniem aplikacji OLE DB należy wziąć pod uwagę następujące problemy:

## <a name="what-programming-implementation-will-you-use-to-write-your-ole-db-application"></a>Jakiej implementacji programowania będziesz używać do pisania aplikacji OLE DB?

Firma Microsoft oferuje kilka bibliotek do wykonania tego zadania: biblioteki szablonów OLE DB, atrybutów OLE DB i nieprzetworzonych interfejsów OLE DB w OLE DB SDK. Ponadto istnieją kreatory, które pomagają napisać program. Te implementacje są opisane w [OLE DB szablony, atrybuty i inne implementacje](../../data/oledb/ole-db-templates-attributes-and-other-implementations.md).

## <a name="do-you-need-to-write-your-own-provider"></a>Czy musisz napisać własnego dostawcę?

Większość deweloperów nie musi pisać własnego dostawcy. Firma Microsoft udostępnia kilku dostawcom. Za każdym razem, gdy tworzone jest połączenie danych (na przykład podczas dodawania odbiorcy do projektu za pomocą **kreatora ATL OLE DB Consumer**), okno dialogowe **Właściwości łącza danych** zawiera listę wszystkich dostępnych dostawców zarejestrowanych w systemie. Jeśli jeden z dostawców jest odpowiedni dla własnego magazynu danych i aplikacji do uzyskiwania dostępu do danych, najłatwiejszym rozwiązaniem jest użycie jednego z nich. Jeśli jednak magazyn danych nie pasuje do jednej z tych kategorii, należy utworzyć własnego dostawcę. Aby uzyskać informacje na temat tworzenia dostawców, zobacz [OLE DB szablonów dostawców](../../data/oledb/ole-db-provider-templates-cpp.md).

## <a name="what-level-of-support-do-you-need-for-your-consumer"></a>Jakiego poziomu pomocy technicznej potrzebujesz dla konsumenta?

Niektórzy klienci mogą być podstawową. inne mogą być złożone. Funkcja obiektów OLE DB jest określana przez właściwości. W przypadku utworzenia dostawcy za pomocą **kreatora ATL OLE DB klienta** programu lub **Kreatora dostawcy bazy danych** ustawia on odpowiednie właściwości obiektu, aby zapewnić standardowy zestaw funkcji. Jeśli jednak klasy klienta lub dostawcy generowane przez kreatora nie obsługują wszystkiego, czego potrzebujesz, należy odwołać się do interfejsów dla tych klas w [bibliotece szablonów OLE DB](../../data/oledb/ole-db-templates.md). Te interfejsy zawijają nieprzetworzone interfejsy OLE DB, zapewniając dodatkową implementację, aby ułatwić korzystanie z nich.

Na przykład jeśli chcesz zaktualizować dane w zestawie wierszy, ale nie chcesz go określić podczas tworzenia konsumenta przy użyciu kreatora, możesz określić funkcje po tym fakcie, ustawiając `DBPROP_IRowsetChange` właściwości i `DBPROP_UPDATABILITY` w obiekcie Command. Następnie, gdy zestaw wierszy zostanie utworzony, ma `IRowsetChange` interfejs.

## <a name="do-you-have-older-code-using-another-data-access-technology-ado-odbc-or-dao"></a>Czy masz starszy kod korzystający z innej technologii dostępu do danych (ADO, ODBC lub DAO)?

Uwzględniając możliwe kombinacje technologii (takich jak używanie składników ADO ze składnikami OLE DB i migrowanie kodu ODBC do OLE DB), obejmując wszystkie sytuacje, wykraczając poza zakres C++ dokumentacji wizualnej. Wiele artykułów obejmujących różne scenariusze jest jednak dostępnych w następujących witrynach sieci Web firmy Microsoft:

- [Pomoc i obsługa techniczna firmy Microsoft](https://support.microsoft.com/)

- [Artykuły techniczne dotyczące dostępu do danych firmy Microsoft — Omówienie](/previous-versions/ms810811(v=msdn.10))

## <a name="see-also"></a>Zobacz także

[Programowanie OLE DB](../../data/oledb/ole-db-programming.md)<br/>
[Omówienie programowania OLE DB](../../data/oledb/ole-db-programming-overview.md)
