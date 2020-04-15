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
ms.openlocfilehash: f65a7b7afcf6bd832c9c23560bb29374038fae1b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370442"
---
# <a name="tn002-persistent-object-data-format"></a>TN002: format trwałych danych obiektu

W tej notatce opisano procedury MFC, które obsługują trwałe obiekty C++ i format danych obiektu, gdy są przechowywane w pliku. Dotyczy to tylko klas z [makrami DECLARE_SERIAL](../mfc/reference/run-time-object-model-services.md#declare_serial) i [IMPLEMENT_SERIAL.](../mfc/reference/run-time-object-model-services.md#implement_serial)

## <a name="the-problem"></a>The Problem

Implementacja MFC dla danych trwałych przechowuje dane dla wielu obiektów w jednej ciągłej części pliku. `Serialize` Metoda obiektu tłumaczy dane obiektu na kompaktowy format binarny.

Implementacja gwarantuje, że wszystkie dane są zapisywane w tym samym formacie przy użyciu [CArchive Class](../mfc/reference/carchive-class.md). Używa `CArchive` obiektu jako tłumacza. Ten obiekt utrzymuje się od momentu jego utworzenia, dopóki nie zostanie [wywołany CArchive::Close](../mfc/reference/carchive-class.md#close). Ta metoda może być wywoływana jawnie przez programistę lub niejawnie przez destruktora, gdy program kończy działanie zakresu, który zawiera `CArchive`.

W tej notatce `CArchive` opisano implementację elementów [członkowskich CArchive::ReadObject](../mfc/reference/carchive-class.md#readobject) i [CArchive::WriteObject](../mfc/reference/carchive-class.md#writeobject). Kod tych funkcji można znaleźć w arcobj.cpp, a `CArchive` główna implementacja w Arccore.cpp. Kod użytkownika nie `ReadObject` `WriteObject` dzwoni i bezpośrednio. Zamiast tego obiekty te są używane przez operatory wstawiania i wyodrębniania specyficzne dla klasy, które są generowane automatycznie przez makra DECLARE_SERIAL i IMPLEMENT_SERIAL. Poniższy kod `WriteObject` pokazuje, jak i `ReadObject` są niejawnie wywoływane:

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

Metoda `CArchive::WriteObject` zapisuje dane nagłówka, który jest używany do rekonstrukcji obiektu. Dane te składają się z dwóch części: typu obiektu i stanu obiektu. Ta metoda jest również odpowiedzialny za utrzymanie tożsamości obiektu są zapisywane, tak, że tylko jedna kopia jest zapisywany, niezależnie od liczby wskaźników do tego obiektu (w tym wskaźniki kołowe).

Zapisywanie (wstawianie) i przywracanie (wyodrębnianie) obiektów opiera się na kilku "stałych manifestu." Są to wartości, które są przechowywane w formacie binarnym i dostarczają ważnych informacji do archiwum (uwaga prefiks "w" wskazuje ilości 16-bitowe):

|Tag|Opis|
|---------|-----------------|
|wNullTag|Używane dla wskaźników obiektów NULL (0).|
|wNewClassTag|Wskazuje opis klasy, który następuje jest nowy w tym kontekście archiwum (-1).|
|wOldClassTag (Nieumiejeć)|Wskazuje, że klasa odczytanego obiektu została widoczna w tym kontekście (0x8000).|

Podczas przechowywania obiektów archiwum przechowuje [CMapPtrToPtr](../mfc/reference/cmapptrtoptr-class.md) *(m_pStoreMap),* który jest mapowaniem z przechowywanego obiektu do 32-bitowego identyfikatora trwałego (PID). Identyfikator PID jest przypisywany do każdego unikatowego obiektu i każdej unikatowej nazwy klasy zapisanej w kontekście archiwum. Te PID są rozdawane kolejno, począwszy od 1. Te identyfikatory PID nie mają znaczenia poza zakresem archiwum, a w szczególności nie należy ich mylić z numerami rekordów lub innymi elementami tożsamości.

W `CArchive` klasie PID są 32-bitowe, ale są wypisywane jako 16-bitowe, chyba że są większe niż 0x7FFE. Duże pids są zapisywane jako 0x7FFF następuje 32-bitowy PID. Utrzymuje to zgodność z projektami, które zostały utworzone we wcześniejszych wersjach.

Gdy zostanie wykonane żądanie zapisania obiektu w archiwum (zwykle przy użyciu globalnego operatora wstawiania), sprawdza się wskaźnik [CObject](../mfc/reference/cobject-class.md) null. Jeśli wskaźnik ma wartość NULL, *wNullTag* zostanie wstawiony do strumienia archiwum.

Jeśli wskaźnik nie jest null i mogą być `DECLARE_SERIAL` serializowane (klasa jest klasą), kod sprawdza *m_pStoreMap,* aby zobaczyć, czy obiekt został już zapisany. Jeśli tak, kod wstawia 32-bitowy identyfikator PID skojarzony z tym obiektem do strumienia archiwum.

Jeśli obiekt nie został zapisany wcześniej, istnieją dwie możliwości do rozważenia: zarówno obiekt, jak i dokładny typ (czyli klasa) obiektu są nowe w tym kontekście archiwum lub obiekt jest dokładnie widoczny. Aby ustalić, czy typ został widoczna, kod wysyła zapytanie *m_pStoreMap* dla obiektu `CRuntimeClass` [CRuntimeClass,](../mfc/reference/cruntimeclass-structure.md) który pasuje do obiektu skojarzonego z zapisywanym obiektem. Jeśli istnieje dopasowanie, `WriteObject` wstawia tag, który `OR` jest bit-wise *wOldClassTag* i tego indeksu. Jeśli `CRuntimeClass` jest nowy w tym `WriteObject` kontekście archiwum, przypisuje nowy identyfikator PID do tej klasy i wstawia go do archiwum, poprzedzone *wartością wNewClassTag.*

Deskryptor dla tej klasy jest następnie wstawiany do archiwum przy użyciu `CRuntimeClass::Store` metody. `CRuntimeClass::Store`wstawia numer schematu klasy (patrz poniżej) i nazwę tekstową ASCII klasy. Należy zauważyć, że użycie nazwy tekstowej ASCII nie gwarantuje unikatowości archiwum w aplikacjach. W związku z tym należy oznaczyć pliki danych, aby zapobiec uszkodzeniu. Po wstawieniu informacji o klasie archiwum umieszcza obiekt w *m_pStoreMap,* a następnie wywołuje `Serialize` metodę wstawiania danych specyficznych dla klasy. Umieszczenie obiektu w *m_pStoreMap* przed wywołaniem `Serialize` zapobiega zapisywaniu wielu kopii obiektu w magazynie.

Podczas powrotu do początkowego wywołującego (zwykle głównego katalogu sieci obiektów), należy wywołać [CArchive::Close](../mfc/reference/carchive-class.md#close). Jeśli planujesz wykonać inne operacje [CFile,](../mfc/reference/cfile-class.md)należy wywołać `CArchive` metodę [Flush,](../mfc/reference/carchive-class.md#flush) aby zapobiec uszkodzeniu archiwum.

> [!NOTE]
> Ta implementacja nakłada twardy limit indeksów 0x3FFFFFFE na kontekst archiwum. Liczba ta reprezentuje maksymalną liczbę unikatowych obiektów i klas, które mogą być zapisywane w jednym archiwum, ale pojedynczy plik dysku może mieć nieograniczoną liczbę kontekstów archiwum.

## <a name="loading-objects-from-the-store-carchivereadobject"></a>Ładowanie obiektów ze sklepu (CArchive::ReadObject)

Ładowanie (wyodrębnianie) obiektów `CArchive::ReadObject` używa metody i `WriteObject`jest odwrotnie . Podobnie `WriteObject`jak `ReadObject` w , nie jest wywoływana bezpośrednio przez kod użytkownika; kod użytkownika powinien wywołać operator wyodrębniania typu, który wywołuje `ReadObject` z oczekiwanym `CRuntimeClass`. Ubezpiecza to integralność typu operacji wyodrębniania.

Ponieważ `WriteObject` implementacja przypisane zwiększenie identyfikatorów PID, począwszy od 1 (0 `ReadObject` jest wstępnie zdefiniowane jako null obiektu), implementacja może używać tablicy do utrzymania stanu kontekstu archiwum. Gdy identyfikator PID jest odczytywany ze sklepu, jeśli identyfikator PID jest `ReadObject` większy niż bieżąca górna granica *m_pLoadArray,* wie, że następuje nowy obiekt (lub opis klasy).

## <a name="schema-numbers"></a>Numery schematów

Numer schematu, który jest przypisany do `IMPLEMENT_SERIAL` klasy, gdy napotkana jest metoda klasy, jest "wersja" implementacji klasy. Schemat odnosi się do implementacji klasy, a nie do liczby razy dany obiekt został złożony trwałe (zwykle określane jako wersja obiektu).

Jeśli zamierzasz zachować kilka różnych implementacji tej samej klasy w czasie, zwiększanie schematu podczas poprawiania implementacji `Serialize` metody obiektu umożliwi pisanie kodu, który może ładować obiekty przechowywane przy użyciu starszych wersji implementacji.

Metoda `CArchive::ReadObject` będzie rzucać [CArchiveException,](../mfc/reference/carchiveexception-class.md) gdy napotka numer schematu w magazynie trwałym, który różni się od numeru schematu opisu klasy w pamięci. Nie jest łatwo odzyskać z tego wyjątku.

Można użyć `VERSIONABLE_SCHEMA` w połączeniu z (bitowe **LUB)** wersji schematu, aby zachować ten wyjątek od zgłaszanych. Za `VERSIONABLE_SCHEMA`pomocą , kod można podjąć `Serialize` odpowiednie działania w jego funkcji, sprawdzając wartość zwracaną z [CArchive::GetObjectSchema](../mfc/reference/carchive-class.md#getobjectschema).

## <a name="calling-serialize-directly"></a>Wywołanie serializacji bezpośrednio

W wielu przypadkach obciążenie ogólnego schematu `WriteObject` `ReadObject` archiwum obiektów i nie jest konieczne. Jest to typowy przypadek serializacji danych do [CDocument](../mfc/reference/cdocument-class.md). W takim przypadku `Serialize` metoda `CDocument` jest wywoływana bezpośrednio, a nie z operatorami wyciągu lub płytki. Zawartość dokumentu może z kolei korzystać z bardziej ogólnego schematu archiwizacji obiektów.

Bezpośrednie `Serialize` dzwonienie ma następujące zalety i wady:

- Żadne dodatkowe bajty nie są dodawane do archiwum przed lub po serializacji obiektu. To nie tylko zmniejsza zapisane dane, ale `Serialize` umożliwia implementowanie procedur, które mogą obsługiwać dowolne formaty plików.

- MFC jest dostrojony, więc `WriteObject` implementacje `ReadObject` i kolekcje pokrewne nie będą połączone z aplikacją, chyba że potrzebujesz bardziej ogólnego schematu archiwum obiektów do innego celu.

- Kod nie musi być odzyskiwać dane ze starych numerów schematu. Dzięki temu kod serializacji dokumentu jest odpowiedzialny za kodowanie numerów schematów, numerów wersji formatu plików lub niezależnie od liczby identyfikującej używanej na początku plików danych.

- Każdy obiekt, który jest serializowany z bezpośrednim wywołaniem nie `Serialize` może używać `CArchive::GetObjectSchema` lub musi obsługiwać zwracaną wartość (UINT)-1 wskazując, że wersja była nieznana.

Ponieważ `Serialize` jest wywoływana bezpośrednio w dokumencie, zwykle nie jest możliwe dla pod-obiektów dokumentu do archiwizacji odwołań do dokumentu nadrzędnego. Obiekty te muszą mieć wskaźnik do ich dokumentu kontenera jawnie lub należy użyć [CArchive::MapObject](../mfc/reference/carchive-class.md#mapobject) funkcji mapowania `CDocument` wskaźnika do PID przed te tylne wskaźniki są archiwizowane.

Jak wspomniano wcześniej, należy zakodować informacje o `Serialize` wersji i klasie samodzielnie podczas wywoływania bezpośrednio, umożliwiając późniejszą zmianę formatu przy zachowaniu zgodności z poprzednimi wersjami ze starszymi plikami. Funkcja `CArchive::SerializeClass` może być wywoływana jawnie przed bezpośrednio serializacji obiektu lub przed wywołaniem klasy podstawowej.

## <a name="see-also"></a>Zobacz też

[Uwagi techniczne według numerów](../mfc/technical-notes-by-number.md)<br/>
[Uwagi techniczne według kategorii](../mfc/technical-notes-by-category.md)
