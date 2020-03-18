---
title: 'TN002: format trwałych danych obiektu'
ms.date: 11/04/2016
helpviewer_keywords:
- VERSIONABLE_SCHEMA macro [MFC]
- persistent object data
- CArchive class [MFC], support for persistent data
- persistent C++ objects [MFC]
- TN002
ms.assetid: 553fe01d-c587-4c8d-a181-3244a15c2be9
ms.openlocfilehash: 1880d5d43055966dea8ab16dc4f26bd4e4602ec5
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447127"
---
# <a name="tn002-persistent-object-data-format"></a>TN002: format trwałych danych obiektu

Ta Uwaga opisuje procedury MFC obsługujące trwałe C++ obiekty i format danych obiektów, gdy są przechowywane w pliku. Dotyczy to tylko klas z makrami [DECLARE_SERIAL](../mfc/reference/run-time-object-model-services.md#declare_serial) i [IMPLEMENT_SERIAL](../mfc/reference/run-time-object-model-services.md#implement_serial) .

## <a name="the-problem"></a>Problem

Implementacja MFC w przypadku trwałych danych przechowuje dane dla wielu obiektów w pojedynczej ciągłej części pliku. Metoda `Serialize` obiektu tłumaczy dane obiektu na kompaktowy format binarny.

Implementacja gwarantuje, że wszystkie dane są zapisywane w tym samym formacie za pomocą [klasy CArchive](../mfc/reference/carchive-class.md). Używa obiektu `CArchive` jako translator. Ten obiekt jest trwały od momentu utworzenia, dopóki nie zostanie wywołana [CArchive:: Close](../mfc/reference/carchive-class.md#close). Ta metoda może być wywoływana jawnie przez programistę lub niejawnie przez destruktor, gdy program opuszcza zakres zawierający `CArchive`.

Ta Uwaga zawiera opis implementacji elementów członkowskich `CArchive` [CArchive:: ReadObject](../mfc/reference/carchive-class.md#readobject) i [CArchive:: WriteObject](../mfc/reference/carchive-class.md#writeobject). Kod dla tych funkcji można znaleźć w Arcobj. cpp, a główna implementacja `CArchive` w Arccore. cpp. Kod użytkownika nie wywołuje `ReadObject` i `WriteObject` bezpośrednio. Zamiast tego obiekty te są używane przez operatory wstawiania i wyodrębniania bezpieczne dla typów, które są generowane automatycznie przez DECLARE_SERIAL i IMPLEMENT_SERIAL makra. Poniższy kod pokazuje, jak `WriteObject` i `ReadObject` są wywoływane niejawnie:

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

## <a name="saving-objects-to-the-store-carchivewriteobject"></a>Zapisywanie obiektów w magazynie (CArchive:: WriteObject)

Metoda `CArchive::WriteObject` zapisuje dane nagłówka, które są używane do odtworzenia obiektu. Te dane składają się z dwóch części: typu obiektu i stanu obiektu. Ta metoda jest również odpowiedzialna za utrzymywanie tożsamości zapisywanych obiektów, tak aby tylko jedna kopia była zapisywana, niezależnie od liczby wskaźników do tego obiektu (w tym wskaźników okrągłych).

Zapisywanie (wstawianie) i przywracanie (wyodrębnianie) obiektów polega na kilku "stałych manifestu". Są to wartości, które są przechowywane w formacie binarnym i zawierają ważne informacje dla archiwum (należy zwrócić uwagę, że prefiks "w" wskazuje liczbę 16-bitową):

|Tag|Opis|
|---------|-----------------|
|wNullTag|Używane dla wskaźników obiektu o wartości NULL (0).|
|wNewClassTag|Wskazuje, że Poniższy opis klasy jest nowy dla tego kontekstu archiwum (-1).|
|wOldClassTag|Wskazuje klasę odczytywanego obiektu w tym kontekście (0x8000).|

W przypadku przechowywania obiektów archiwum utrzymuje [CMapPtrToPtr](../mfc/reference/cmapptrtoptr-class.md) ( *m_pStoreMap*), który jest mapowaniem z zapisanego obiektu na 32-bitowy identyfikator trwały (PID). Identyfikator PID jest przypisywany do każdego unikatowego obiektu i każdej unikatowej nazwy klasy, która jest zapisywana w kontekście archiwum. Te identyfikatory PID są przekazywane sekwencyjnie, począwszy od 1. Te identyfikatory PID nie mają znaczenia poza zakresem archiwum i, w szczególności, nie należy mylić z numerami rekordów ani innymi elementami tożsamości.

W klasie `CArchive` identyfikatory PID są 32-bitowe, ale są zapisywane jako 16-bitowe, chyba że są większe niż 0x7FFE. Duże identyfikatory PID są zapisywane jako 0x7FFF, po których następuje 32-bitowy Identyfikator PID. Zapewnia to zgodność z projektami, które zostały utworzone we wcześniejszych wersjach.

Gdy zostanie wysłane żądanie zapisania obiektu do archiwum (zazwyczaj przy użyciu globalnego operatora wstawiania), jest wykonywane sprawdzenie dla wskaźnika [CObject](../mfc/reference/cobject-class.md) o wartości null. Jeśli wskaźnik ma wartość NULL, *wNullTag* zostanie wstawiony do strumienia archiwum.

Jeśli wskaźnik nie ma wartości NULL i może być serializowany (Klasa jest klasą `DECLARE_SERIAL`), kod sprawdza *m_pStoreMap* , aby sprawdzić, czy obiekt został już zapisany. Jeśli ma, kod wstawia 32-bitowy Identyfikator PID skojarzony z tym obiektem do strumienia archiwum.

Jeśli obiekt nie został wcześniej zapisany, istnieją dwie metody, które należy wziąć pod uwagę: zarówno obiekt, jak i dokładny typ (czyli Klasa) obiektu są nowe dla tego kontekstu archiwum lub obiekt jest dokładnym już widzianym typem. Aby określić, czy typ był widoczny, kod wysyła zapytanie do *m_pStoreMap* obiektu [CRuntimeClass](../mfc/reference/cruntimeclass-structure.md) , który pasuje do obiektu `CRuntimeClass` skojarzonego z zapisywanym obiektem. Jeśli istnieje dopasowanie, `WriteObject` Wstawia znacznik, który jest `OR`em niestandardowym *wOldClassTag* i tym indeksem. Jeśli `CRuntimeClass` jest nowy w tym kontekście archiwum, `WriteObject` przypisuje nowy identyfikator PID do tej klasy i wstawia go do archiwum, poprzedzone przez wartość *wNewClassTag* .

Deskryptor tej klasy jest następnie wstawiany do archiwum przy użyciu metody `CRuntimeClass::Store`. `CRuntimeClass::Store` wstawia numer schematu klasy (patrz poniżej) i nazwę tekstu ASCII klasy. Należy zauważyć, że użycie nazwy tekstowej ASCII nie gwarantuje unikatowej wartości Archiwum w aplikacjach. W związku z tym należy oznaczyć pliki danych, aby zapobiec uszkodzeniu. Po wstawieniu informacji o klasie archiwum umieszcza obiekt w *m_pStoreMap* a następnie wywołuje metodę `Serialize`, aby wstawić dane specyficzne dla klasy. Umieszczenie obiektu w *m_pStoreMap* przed wywołaniem `Serialize` uniemożliwia zapisanie wielu kopii obiektu w sklepie.

Podczas powrotu do początkowego obiektu wywołującego (zazwyczaj jest to katalog główny sieci obiektów), należy wywołać [CArchive:: Close](../mfc/reference/carchive-class.md#close). Jeśli planujesz wykonać inne operacje [CFile](../mfc/reference/cfile-class.md), musisz wywołać [opróżnianie](../mfc/reference/carchive-class.md#flush) metody `CArchive`, aby zapobiec uszkodzeniu archiwum.

> [!NOTE]
>  Ta implementacja nakłada sztywny limit 0x3FFFFFFE indeksów na kontekst archiwum. Ta liczba reprezentuje maksymalną liczbę unikatowych obiektów i klas, które można zapisać w jednym archiwum, ale jeden plik dysku może mieć nieograniczoną liczbę kontekstów archiwum.

## <a name="loading-objects-from-the-store-carchivereadobject"></a>Ładowanie obiektów ze sklepu (CArchive:: ReadObject)

Ładowanie (wyodrębnianie) obiektów używa metody `CArchive::ReadObject` i jest odwrotnością `WriteObject`. Podobnie jak w przypadku `WriteObject`, `ReadObject` nie jest wywoływana bezpośrednio przez kod użytkownika; kod użytkownika powinien wywołać operator wyodrębniania bezpiecznego typu, który wywołuje `ReadObject` o oczekiwanym `CRuntimeClass`. Spowoduje to, że integralność typu operacji wyodrębniania.

Ponieważ implementacja `WriteObject` przypisała rosnące identyfikatory PID, począwszy od 1 (0 jest wstępnie zdefiniowane jako obiekt NULL), implementacja `ReadObject` może użyć tablicy do utrzymania stanu kontekstu archiwum. Gdy identyfikator PID jest odczytywany ze sklepu, jeśli Identyfikator PID jest większy niż bieżący górny granica *m_pLoadArray*, `ReadObject` wie, że jest następujący nowy obiekt (lub opis klasy).

## <a name="schema-numbers"></a>Numery schematów

Numer schematu, który jest przypisany do klasy podczas napotkania metody `IMPLEMENT_SERIAL` klasy, jest "wersja" implementacji klasy. Schemat odwołuje się do implementacji klasy, a nie liczby przypadków, w których dany obiekt został trwały (zwykle określany jako wersja obiektu).

Jeśli zamierzasz zachować kilka różnych implementacji tej samej klasy z upływem czasu, zwiększając schemat w miarę zmiany implementacji metody `Serialize` obiektu, umożliwi to napisać kod, który może ładować obiekty przechowywane przy użyciu starszych wersji implementacji.

Metoda `CArchive::ReadObject` generuje [CArchiveException](../mfc/reference/carchiveexception-class.md) , gdy napotka numer schematu w magazynie trwałym, który różni się od numeru schematu opisu klasy w pamięci. Odzyskiwanie z tego wyjątku nie jest łatwe.

Aby zapobiec zgłaszaniu tego wyjątku, można użyć `VERSIONABLE_SCHEMA` połączone z (bitową **lub**) wersją schematu. Korzystając z `VERSIONABLE_SCHEMA`, kod może wykonać odpowiednią akcję w funkcji `Serialize`, sprawdzając wartość zwracaną z [CArchive:: GetObjectSchema](../mfc/reference/carchive-class.md#getobjectschema).

## <a name="calling-serialize-directly"></a>Bezpośrednie wywoływanie serializacji

W wielu przypadkach obciążenie ogólnego schematu archiwum obiektów `WriteObject` i `ReadObject` nie jest konieczne. Jest to typowy przypadek serializowania danych do [CDocument](../mfc/reference/cdocument-class.md). W tym przypadku Metoda `Serialize` `CDocument` jest wywoływana bezpośrednio, a nie z operatorami Extract lub INSERT. Zawartość dokumentu może być używana przez bardziej ogólny schemat archiwum obiektów.

Wywoływanie `Serialize` bezpośrednio ma następujące zalety i wady:

- Nie dodano żadnych dodatkowych bajtów do archiwum przed lub po serializacji obiektu. To nie tylko powoduje, że zapisane dane są mniejsze, ale umożliwiają wdrożenie procedur `Serialize`, które mogą obsługiwać wszystkie formaty plików.

- MFC jest dostrojona, dlatego implementacje `WriteObject` i `ReadObject` i powiązane kolekcje nie będą połączone z aplikacją, chyba że potrzebny jest bardziej ogólny schemat archiwum obiektów w innym celu.

- Kod nie musi odzyskać ze starych numerów schematów. Dzięki temu kod serializacji dokumentu jest odpowiedzialny za kodowanie numerów schematu, numery wersji formatu plików lub inne identyfikujące numery używane na początku plików danych.

- Każdy obiekt, który jest serializowany z bezpośrednim wywołaniem do `Serialize` nie może używać `CArchive::GetObjectSchema` lub musi obsługiwać zwracaną wartość (UINT)-1 wskazującą, że wersja była nieznana.

Ponieważ `Serialize` jest wywoływana bezpośrednio w dokumencie, nie jest to zwykle możliwe w przypadku obiektów podrzędnych dokumentu do archiwizowania odwołań do ich dokumentu nadrzędnego. Te obiekty muszą mieć bezpośrednio wskaźnik do swojego dokumentu kontenera lub należy użyć funkcji [CArchive:: MapObject](../mfc/reference/carchive-class.md#mapobject) , aby zmapować wskaźnik `CDocument` na identyfikator PID przed zarchiwizowaniem tych wskaźników wstecznych.

Jak wspomniano wcześniej, należy zakodować informacje o wersji i klasie samodzielnie, gdy wywołasz `Serialize` bezpośrednio, co umożliwi zmianę formatu później przy zachowaniu zgodności z poprzednimi wersjami ze starszymi plikami. Funkcję `CArchive::SerializeClass` można wywołać jawnie przed przystąpieniem do bezpośredniego serializacji obiektu lub przed wywołaniem klasy bazowej.

## <a name="see-also"></a>Zobacz też

[Uwagi techniczne według numerów](../mfc/technical-notes-by-number.md)<br/>
[Uwagi techniczne według kategorii](../mfc/technical-notes-by-category.md)
