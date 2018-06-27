---
title: 'TN002: Format trwałych danych obiektu | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.data
dev_langs:
- C++
helpviewer_keywords:
- VERSIONABLE_SCHEMA macro [MFC]
- persistent object data
- CArchive class [MFC], support for persistent data
- persistent C++ objects [MFC]
- TN002
ms.assetid: 553fe01d-c587-4c8d-a181-3244a15c2be9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: deca5e0913013e73188e505935d5b2c9b8bf79db
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2018
ms.locfileid: "36952212"
---
# <a name="tn002-persistent-object-data-format"></a>TN002: format trwałych danych obiektu
Ta uwaga opisano procedury MFC, które obsługuje obiekty trwałe C++ i format danych obiektu, gdy jest on przechowywany w pliku. Dotyczy to tylko klas z [declare_serial —](../mfc/reference/run-time-object-model-services.md#declare_serial) i [implement_serial —](../mfc/reference/run-time-object-model-services.md#implement_serial) makra.  
  
## <a name="the-problem"></a>Problem  
 Implementacja MFC dla trwałych danych przechowuje dane dla wielu obiektów w jednym ciągłe części pliku. Obiektu `Serialize` metody tłumaczy danych obiektu na format binarny compact.  
  
 Implementacja gwarantuje, że wszystkie dane zostały zapisane w tym samym formacie za pomocą [CArchive — klasa](../mfc/reference/carchive-class.md). Używa `CArchive` obiektu jako translatora. Ten obiekt będzie się powtarzać od czasu do czasu wywołania jest tworzona [CArchive::Close](../mfc/reference/carchive-class.md#close). Tę metodę można wywołać jawnie przez programistę albo niejawnie przez destruktor gdy program jest kończona zakresu, który zawiera `CArchive`.  
  
 Ta uwaga opisuje wykonania `CArchive` członków [CArchive::ReadObject](../mfc/reference/carchive-class.md#readobject) i [CArchive::WriteObject](../mfc/reference/carchive-class.md#writeobject). Można znaleźć kod dla tych funkcji w Arcobj.cpp i głównym implementacji dla `CArchive` w Arccore.cpp. Kod użytkownika wywołuje `ReadObject` i `WriteObject` bezpośrednio. Zamiast tego te obiekty są używane przez specyficzne bezpieczne wstawiania i wyodrębniania operatorów, które są generowane automatycznie przez declare_serial — i implement_serial — makra. Poniższy kod przedstawia sposób `WriteObject` i `ReadObject` wywoływany niejawnie:  
  
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
  
## <a name="saving-objects-to-the-store-carchivewriteobject"></a>Zapisywanie obiektów w magazynie (CArchive::WriteObject)  
 Metoda `CArchive::WriteObject` zapisuje dane nagłówka, używany do rekonstrukcji obiektu. Te dane składa się z dwóch części: typ obiektu i stanu obiektu. Ta metoda jest również odpowiedzialny za konserwację tożsamości obiektu zapisywana, aby były zapisywane tylko jednej kopii, niezależnie od liczby wskaźników do tego obiektu (w tym wskaźniki cykliczne).  
  
 Zapisywanie (Wstawianie) i przywracanie obiektów (wyodrębnianie) opiera się na kilka "manifestu stałych." Poniżej przedstawiono wartości, które są przechowywane w pliku binarnego i zawierają istotne informacje do archiwum (Uwaga prefiksem "t" oznacza ilości 16-bitowych):  
  
|Tag|Opis|  
|---------|-----------------|  
|wNullTag|Używany do wskaźników obiektu NULL (0).|  
|wNewClassTag|Wskazuje, że opis klasy, który następuje jest nowym składnikiem tego kontekstu archiwum (-1).|  
|wOldClassTag|Wskazuje, że zarejestrowano klasę obiektu odczytywane w tym kontekście (0x8000).|  
  
 W przypadku przechowywania obiektów, archiwum przechowuje [CMapPtrToPtr](../mfc/reference/cmapptrtoptr-class.md) ( *m_pStoreMap*) czyli mapowanie obiektu przechowywane do 32-bitowy identyfikator trwałe (PID). Identyfikator procesu jest przypisany do każdego obiektu unikatowy i co unikalną nazwę klasy zapisaną w kontekście archiwum. Te PID są przekazać sekwencyjnie rozpoczyna się od 1. PID te nie mają znaczenia poza zakresem archiwum i są w szczególności nie należy mylić z numery rekordów lub innych elementów tożsamości.  
  
 W `CArchive` klasy, PID są 32-bitowe, ale są one zapisywane jako 16-bitowych, chyba że są większe niż 0x7FFE. Duże PID są zapisywane jako 0x7FFF następuje 32-bitowy identyfikator PID procesu. To zapewnia zgodność z projektów, które zostały utworzone we wcześniejszych wersjach.  
  
 Po wysłaniu żądania jest można zapisać obiektu do archiwum (zazwyczaj za pomocą operatora wstawiania globalne), dokonuje null [CObject](../mfc/reference/cobject-class.md) wskaźnika. Jeśli wskaźnik jest pusty, *wNullTag* są wstawiane do strumienia archiwum.  
  
 Jeśli wskaźnik nie jest równa NULL i może być Zserializowany (klasa `DECLARE_SERIAL` klasy), kontroli kodu *m_pStoreMap* aby zobaczyć, czy obiekt został już zapisany. Jeśli ma ona kod wstawia 32-bitowego identyfikatora PID skojarzone z tym obiektem do strumienia archiwum.  
  
 Jeśli obiekt nie został zapisany przed, istnieją dwie możliwości wziąć pod uwagę: zarówno obiekt i dokładne typ (czyli klasa) obiektu dopiero zaczynasz korzystać z tego kontekstu archiwum albo obiekt jest typu dokładne już widoczny. Aby ustalić, czy typ została napotkana, zapytania kod *m_pStoreMap* dla [CRuntimeClass](../mfc/reference/cruntimeclass-structure.md) obiekt, który jest zgodny `CRuntimeClass` obiekt skojarzony z obiektem zapisywany. Jeśli istnieje dopasowanie, `WriteObject` wstawia znacznik, który jest operacja `OR` z *wOldClassTag* i tego indeksu. Jeśli `CRuntimeClass` jest nowa w tym kontekście archiwum `WriteObject` przypisuje nowego identyfikatora PID do tej klasy i wstawia go do archiwum poprzedzony *wNewClassTag* wartości.  
  
 Deskryptor dla tej klasy zostanie wstawiony na za pomocą archiwum `CRuntimeClass::Store` metody. `CRuntimeClass::Store` Wstawia numer schematu klasy (patrz poniżej) i nazwę klasy tekstu ASCII. Należy pamiętać, że użycie nazwy tekstu ASCII nie gwarantuje unikatowości archiwum w aplikacjach. W związku z tym należy oznaczyć pliki danych, aby zapobiec uszkodzeniu. Następujące wstawiania informacji o klasie archiwum umieszcza obiektu do *m_pStoreMap* , a następnie wywołuje `Serialize` metodę, aby wstawić dane specyficzne dla klasy. Wprowadzenie do obiektu do *m_pStoreMap* przed wywołaniem `Serialize` uniemożliwia wiele kopii obiektu są zapisywane w magazynie.  
  
 Po powrocie do początkowego wywołującego (zazwyczaj główne sieci obiektów), należy wywołać [CArchive::Close](../mfc/reference/carchive-class.md#close). Jeśli planujesz do wykonywania innych [cfile —](../mfc/reference/cfile-class.md)operacji, należy wywołać `CArchive` metody [opróżnić](../mfc/reference/carchive-class.md#flush) aby zapobiec uszkodzeniu archiwum.  
  
> [!NOTE]
>  Ta implementacja nakłada nienaruszalne ograniczenie indeksów 0x3FFFFFFE na kontekst archiwum. Liczba ta reprezentuje maksymalną liczbę unikatowych obiekty i klasy, które mogą być zapisane w jednym archiwum, ale dysk pojedynczy plik może mieć dowolną liczbę kontekstów archiwum.  
  
## <a name="loading-objects-from-the-store-carchivereadobject"></a>Ładowanie obiektów z magazynu (CArchive::ReadObject)  
 Podczas ładowania (wyodrębnianie) obiektów używa `CArchive::ReadObject` — metoda i jest odwrotnej z `WriteObject`. Jak `WriteObject`, `ReadObject` nie jest wywoływany bezpośrednio przez kod użytkownika; kodu użytkownika powinien wywoływać operator wyodrębniania bezpieczny, który wywołuje `ReadObject` z oczekiwanym `CRuntimeClass`. Dzięki temu integralności typ operacji wyodrębniania.  
  
 Ponieważ `WriteObject` implementacji przypisane zwiększa PID, począwszy od 1 (0 wstępnie zdefiniowane jako obiekt NULL), `ReadObject` implementacji służy do zarządzania stanem kontekstu archiwum tablicy. Podczas odczytu identyfikatora PID ze sklepu, jeśli identyfikator PID jest większy niż bieżący górna granica *m_pLoadArray*, `ReadObject` wie, następuje nowego obiektu (lub opis klasy).  
  
## <a name="schema-numbers"></a>Numery schematu  
 Numer schematu, która jest przypisana do klasy podczas `IMPLEMENT_SERIAL` metody klasy napotkano, to "version" implementacji klasy. Schemat odwołuje się do implementacji klasy, aby liczba razy nie danego obiektu wprowadzono trwałe (zwykle określonych jako wersja obiektu).  
  
 Jeśli planujesz obsługiwać kilka różnych implementacji w tej samej klasy wraz z upływem czasu, zwiększając schematu Popraw nazwę obiektu `Serialize` implementacji metody umożliwi pisania kodu, który można załadować obiekty przechowywane przy użyciu starszych wersji Implementacja.  
  
 `CArchive::ReadObject` Metoda zgłosi [CArchiveException](../mfc/reference/carchiveexception-class.md) po napotkaniu liczbą schematu magazynu trwałego, która różni się od liczby schematu opis klasy w pamięci. Nie jest łatwo odzyskać z poziomu tego wyjątku.  
  
 Można użyć `VERSIONABLE_SCHEMA` połączone z (bitowe **lub**) Twojej wersji schematu, aby zachować ten wyjątek z został zgłoszony. Za pomocą `VERSIONABLE_SCHEMA`, kodu można podjąć odpowiednie działania jego `Serialize` funkcji, sprawdzając wartość zwrotną z elementu [CArchive::GetObjectSchema](../mfc/reference/carchive-class.md#getobjectschema).  
  
## <a name="calling-serialize-directly"></a>Wywoływanie serializować bezpośrednio  
 W wielu przypadkach obciążenie systemu archiwum obiekt ogólny `WriteObject` i `ReadObject` nie jest konieczne. Jest to często zdarza serializowania danych do [CDocument](../mfc/reference/cdocument-class.md). W takim przypadku `Serialize` metoda `CDocument` jest wywoływana bezpośrednio, nie z operatorów wyodrębniania lub insert. Zawartość dokumentu z kolei może używać bardziej ogólne schematu obiektu w archiwum.  
  
 Wywoływanie `Serialize` bezpośrednio ma następujące zalety i wady:  
  
-   Bajty dodatkowych nie są dodawane do archiwum przed lub po serializowany jest obiekt. To nie tylko sprawia, że zapisane dane mniejsze, ale pozwala na wdrożenie `Serialize` procedury, które może obsłużyć wszelkie formaty plików.  
  
-   MFC jest dostosowana tak `WriteObject` i `ReadObject` implementacji i powiązane kolekcje nie zostaną połączone w aplikacji, chyba że potrzebne są bardziej ogólne schematu obiektu w archiwum dla niektórych innych celów.  
  
-   Kod nie ma pozwoli na odzyskanie starego numery schematu. Dzięki temu kodu serializacji dokumentu odpowiedzialny za numery schemat kodowania, numery wersji formatu pliku lub identyfikowania niezależnie od liczby można używać na początku pliki danych.  
  
-   Każdy obiekt, który jest serializowany z bezpośrednie wywołanie `Serialize` nie mogą używać `CArchive::GetObjectSchema` lub musi dojścia zwracana wartość -1 (UINT) wskazujący wersję nieznany.  
  
 Ponieważ `Serialize` jest wywoływana bezpośrednio w dokumencie, nie jest zwykle możliwe w dla obiektów podrzędnych dokumentu w celu archiwizacji odwołania do ich nadrzędnej dokumentu. Te obiekty muszą mieć wskaźnik do ich kontenerem jawnie lub użyć [CArchive::MapObject](../mfc/reference/carchive-class.md#mapobject) funkcja mapowania `CDocument` wskaźnik do identyfikatora PID przed te wskaźniki wstecz zostaną zarchiwizowane.  
  
 Jak wspomniano wcześniej, kodowania wersja i informacje dotyczące klas samodzielnie podczas wywoływania `Serialize` bezpośrednio, dzięki któremu można później zmienić format, zachowując zgodność z poprzednimi wersjami ze starszych wersji plików. `CArchive::SerializeClass` Funkcja może zostać wywołana jawnie przed bezpośrednio szeregowania obiektu lub przed wywołaniem klasy podstawowej.  
  
## <a name="see-also"></a>Zobacz też  
 [Uwagi techniczne według numerów](../mfc/technical-notes-by-number.md)   
 [Uwagi techniczne według kategorii](../mfc/technical-notes-by-category.md)

