---
title: 'TN002: format trwałych danych obiektu'
ms.date: 11/04/2016
f1_keywords:
- vc.data
helpviewer_keywords:
- VERSIONABLE_SCHEMA macro [MFC]
- persistent object data
- CArchive class [MFC], support for persistent data
- persistent C++ objects [MFC]
- TN002
ms.assetid: 553fe01d-c587-4c8d-a181-3244a15c2be9
ms.openlocfilehash: 5f5bde68d9fd4175ed97a7b61d807887d07e9e12
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50474389"
---
# <a name="tn002-persistent-object-data-format"></a>TN002: format trwałych danych obiektu

Ta uwaga opisuje procedury MFC, które obsługują obiekty trwałe C++ i format danych obiektu, gdy jest on przechowywany w pliku. Dotyczy to tylko klasach z atrybutem [DECLARE_SERIAL](../mfc/reference/run-time-object-model-services.md#declare_serial) i [IMPLEMENT_SERIAL](../mfc/reference/run-time-object-model-services.md#implement_serial) makra.

## <a name="the-problem"></a>Ten Problem

Implementacji MFC dla trwałego danych przechowuje dane dla wielu obiektów w jednym ciągłym części pliku. Obiekt `Serialize` metoda tłumaczy danych obiektu na compact format binarny.

Implementacja gwarantuje, że wszystkie dane są zapisywane w tym samym formacie za pomocą [klasie CArchive](../mfc/reference/carchive-class.md). Używa ona `CArchive` obiektu jako translator. Ten obiekt będzie się powtarzać od czasu, jest tworzony, dopóki nie zostanie wywołana [CArchive::Close](../mfc/reference/carchive-class.md#close). Ta metoda może być wywoływana jawnie przez programistę albo niejawnie przez destruktor gdy zamyka program zakres, który zawiera `CArchive`.

Ta uwaga opisuje implementacja `CArchive` członków [CArchive::ReadObject](../mfc/reference/carchive-class.md#readobject) i [CArchive::WriteObject](../mfc/reference/carchive-class.md#writeobject). Zawiera kod dla tych funkcji w Arcobj.cpp i główne implementację dla `CArchive` w Arccore.cpp. Kod użytkownika wywołuje `ReadObject` i `WriteObject` bezpośrednio. Zamiast tego te obiekty są wykorzystywane przez swoiste dla klas bezpieczny wstawienia i wydobycia operatory, które są generowane automatycznie przez DECLARE_SERIAL i IMPLEMENT_SERIAL makra. Poniższy kod przedstawia sposób `WriteObject` i `ReadObject` wywoływany niejawnie:

```
class CMyObject : public CObject
{
    DECLARE_SERIAL(CMyObject)
};

IMPLEMENT_SERIAL(CMyObj, CObject, 1)

// example usage (ar is a CArchive&)
CMyObject* pObj;
CArchive& ar;
ar <<pObj;        // calls ar.WriteObject(pObj)
ar>> pObj;        // calls ar.ReadObject(RUNTIME_CLASS(CObj))
```

## <a name="saving-objects-to-the-store-carchivewriteobject"></a>Zapisywanie obiektów Store (CArchive::WriteObject)

Metoda `CArchive::WriteObject` zapisuje dane nagłówka, umożliwiający odtworzenie obiektu. Te dane, który składa się z dwóch części: typ i stan obiektu. Ta metoda jest również odpowiedzialna za tożsamość obiektu są zapisywane, aby były zapisywane tylko jednej kopii, bez względu na liczbę wskaźników do tego obiektu (w tym wskaźniki cykliczne).

Zapisywanie (Wstawianie) i przywracanie obiektów (wyodrębniania) opiera się na kilka "stałych manifestu." Są to wartości, są przechowywane w pliku binarnym, które zawierają istotne informacje do archiwum (Uwaga prefiksem "t" wskazuje ilości 16-bitowych):

|Tag|Opis|
|---------|-----------------|
|wNullTag|Używane dla wskaźników obiekt o wartości NULL (0).|
|wNewClassTag|Wskazuje, że opis klasy, który następuje po jest nowym składnikiem w tym kontekście archiwum (-1).|
|wOldClassTag|Wskazuje, że klasa obiektu odczytywanych został napotkany w tym kontekście (0x8000).|

W przypadku przechowywania obiektów, archiwum przechowuje [CMapPtrToPtr](../mfc/reference/cmapptrtoptr-class.md) ( *m_pStoreMap*) czyli mapowanie przechowywany obiekt do 32-bitowy identyfikator trwały (PID). Identyfikator PID jest przypisany do każdego obiektu unikatowy i co unikalną nazwę klasy zapisaną w kontekście archiwum. Te identyfikatory PID są przekazywane się sekwencyjnie rozpoczyna się od 1. Te identyfikatory PID nie mają znaczenia poza zakresem archiwum, a w szczególności, to nie należy mylić z rekordu numery lub inne elementy tożsamości.

W `CArchive` klasy, identyfikatory PID są 32-bitowych, ale są one zapisywane jako 16-bitowych, chyba że są one większe niż 0x7FFE. Identyfikatory PID w dużych są zapisywane jako 0x7FFF następuje PID 32-bitowych. Zapewnia to dostępność zgodności z projektami, które zostały utworzone we wcześniejszych wersjach.

Po wysłaniu żądania do zapisania obiektu do archiwum (zazwyczaj przy użyciu operatora wstawiania globalny), dokonuje null [CObject](../mfc/reference/cobject-class.md) wskaźnika. Jeśli wskaźnik jest pusty, *wNullTag* jest wstawiany do strumienia archiwum.

Jeżeli wskaźnik nie jest równa NULL i może być serializowany (klasa jest `DECLARE_SERIAL` klasy), kontroli kodu *m_pStoreMap* aby zobaczyć, czy obiekt został już zapisany. Jeśli tak, kod wstawia 32-bitowego identyfikatora PID skojarzonej z tym obiektem w strumieniu archiwum.

Jeśli obiekt nie został zapisany zanim, istnieją dwie możliwości do rozważenia: obiekt i dokładnego typu (czyli klasa) obiekt zaczynasz tego kontekstu archiwum albo obiekt jest typu dokładnie już widoczne. Aby ustalić, czy typ został napotkany, zapytania kod *m_pStoreMap* dla [CRuntimeClass](../mfc/reference/cruntimeclass-structure.md) obiektu, który odpowiada `CRuntimeClass` obiekt skojarzony z obiektem, trwa zapisywanie. Jeśli istnieje dopasowanie, `WriteObject` wstawia znacznik, który jest operacja `OR` z *wOldClassTag* i tego indeksu. Jeśli `CRuntimeClass` jest nowym składnikiem w tym kontekście archiwum `WriteObject` przypisuje nowy identyfikator PID dla tej klasy i wstawia je do archiwum, poprzedzony *wNewClassTag* wartości.

Deskryptor dla tej klasy zostanie wstawiony do archiwum przy użyciu `CRuntimeClass::Store` metody. `CRuntimeClass::Store` Wstawia numer schematu klasy (patrz poniżej) i ASCII tekstowa Nazwa klasy. Należy pamiętać, że użycie nazwy tekstu ASCII nie gwarantuje unikatowość archiwum w aplikacjach. W związku z tym należy oznaczyć pliki danych, aby zapobiec uszkodzeniu. Następujące wstawiania informacji o klasie archiwum umieszcza obiektu do *m_pStoreMap* , a następnie wywołuje `Serialize` metodę, aby wstawić dane specyficzne dla klasy. Wprowadzenie do obiektu do *m_pStoreMap* przed wywołaniem `Serialize` zapobiega wiele kopii obiektu są zapisywane do magazynu.

Po powrocie do początkowego wywołującego (zwykle katalog główny sieci obiektów), należy wywołać [CArchive::Close](../mfc/reference/carchive-class.md#close). Jeśli planujesz wykonać inne [CFile](../mfc/reference/cfile-class.md)operacji, należy wywołać `CArchive` metoda [opróżniania](../mfc/reference/carchive-class.md#flush) aby zapobiec uszkodzeniu archiwum.

> [!NOTE]
>  Ta implementacja nakłada stały limit 0x3FFFFFFE indeksów w kontekście archiwum. Ta wartość liczbowa określa maksymalną liczbę unikatowych obiektów i klasy, które mogą być zapisane w jednym archiwum, ale plik jednego dysku może mieć dowolną liczbę kontekstów archiwum.

## <a name="loading-objects-from-the-store-carchivereadobject"></a>Trwa ładowanie obiektów z Store (CArchive::ReadObject)

Podczas ładowania (wyodrębnianie) obiektów używa `CArchive::ReadObject` metody i jest przeciwny z `WriteObject`. Podobnie jak w przypadku `WriteObject`, `ReadObject` nie jest wywoływany bezpośrednio przez kod użytkownika; kod użytkownika powinna wywołać operator wyodrębniania bezpiecznegop typu, który wywołuje `ReadObject` przewidywanego `CRuntimeClass`. Dzięki temu integralności typu operacji wyodrębniania.

Ponieważ `WriteObject` implementacji przypisane zwiększa identyfikatory PID, począwszy od 1 (0 wstępnie zdefiniowane jako obiekt o wartości NULL), `ReadObject` implementacji skorzystaj z tablicy do zarządzania stanem kontekstu archiwum. Gdy identyfikatora PID są odczytywane w sklepie, jeśli identyfikator PID jest większy niż bieżący górną granicę *m_pLoadArray*, `ReadObject` wie, następuje nowy obiekt (lub opis klasy).

## <a name="schema-numbers"></a>Numery schematu

Numer schematu, który jest przypisany do klasy podczas `IMPLEMENT_SERIAL` metody klasy zostanie osiągnięty, jest "wersja" Implementacja klasy. Schemat, który odwołuje się do implementacji klasy, nie do liczby godzin danego obiektu złożonego trwałe (zwykle określane jako wersja obiektu).

Jeśli zamierzasz obsługiwać kilka różnych implementacji w tej samej klasy wraz z upływem czasu, zwiększając schematu Popraw nazwę obiektu `Serialize` implementacji metody umożliwią napisać kod, który można załadować obiekty przechowywane przy użyciu starszej wersji Implementacja.

`CArchive::ReadObject` Metoda zgłosi [CArchiveException](../mfc/reference/carchiveexception-class.md) po napotkaniu liczba schematu w magazynie trwałym, która różni się od schematu liczba opis klasy w pamięci. Nie jest łatwo odzyskać z poziomu tego wyjątku.

Możesz użyć `VERSIONABLE_SCHEMA` w połączeniu z (bitowe **lub**) Twojej wersji schematu, aby zachować ten wyjątek z zgłaszane. Za pomocą `VERSIONABLE_SCHEMA`, Twój kod może podejmij odpowiednie działania jego `Serialize` funkcji, sprawdzając wartość zwrotną z elementu [CArchive::GetObjectSchema](../mfc/reference/carchive-class.md#getobjectschema).

## <a name="calling-serialize-directly"></a>Wywoływanie serializować bezpośrednio

W wielu przypadkach obciążenie systemu archiwum obiekt ogólny `WriteObject` i `ReadObject` nie jest konieczne. Jest to często spotykana szeregowania danych do [CDocument](../mfc/reference/cdocument-class.md). W tym przypadku `Serialize` metoda `CDocument` jest wywoływana bezpośrednio, nie z operatorów wyodrębniania lub insert. Zawartość dokumentu z kolei może używać bardziej ogólne schemat obiektu w archiwum.

Wywoływanie `Serialize` bezpośrednio ma następujące zalety i wady:

- Brak dodatkowych bajtów są dodawane do archiwum przed lub po serializowany jest obiekt. To nie tylko sprawia, że zapisanych danych jest mniejszy, ale pozwala na implementowanie `Serialize` procedur, które może obsłużyć dowolny formaty plików.

- MFC jest ona dostrojona więc `WriteObject` i `ReadObject` implementacji i powiązane kolekcje nie będzie połączony w swojej aplikacji, chyba że potrzebujesz bardziej ogólne schemat obiektu w archiwum dla niektórych innych celów.

- Twój kod ma odzyskać stare numery schematu. To sprawia, że kod serializacji dokumentu odpowiedzialny za kodowania liczby schematu, numery wersji formatu pliku lub identyfikowanie niezależnie od liczby, możesz użyć przy uruchamianiu plików danych.

- Każdy obiekt, który jest serializowana z bezpośrednie wywołanie `Serialize` nie mogą używać `CArchive::GetObjectSchema` lub musi uchwyt zwracana wartość -1 (UINT) wskazująca, że wersja jest nieznany.

Ponieważ `Serialize` jest wywoływana bezpośrednio w dokumencie, nie jest zwykle możliwe podrzędnych obiektów dokumentu w celu archiwizacji odwołania do ich nadrzędnej dokumentu. Te obiekty musi być przyznane wskaźnikiem do swojego dokumentu kontenera lub należy użyć [CArchive::MapObject](../mfc/reference/carchive-class.md#mapobject) funkcję, aby zamapować `CDocument` wskaźnik do identyfikatora PID, zanim te wskaźniki wstecz zostaną zarchiwizowane.

Jak wspomniano wcześniej, kodowanie wersji i informacji klasy samodzielnie po wywołaniu `Serialize` bezpośrednio, dzięki któremu można później zmienić format przy jednoczesnym zachowaniu zgodności z poprzednimi wersjami przy użyciu starszych wersji plików. `CArchive::SerializeClass` Funkcja może zostać wywołana jawnie, przed rozpoczęciem bezpośrednio serializacji obiektu lub przed wywołaniem klasy bazowej.

## <a name="see-also"></a>Zobacz też

[Uwagi techniczne według numerów](../mfc/technical-notes-by-number.md)<br/>
[Uwagi techniczne według kategorii](../mfc/technical-notes-by-category.md)

