---
title: Korzystanie z plików źródłowych MFC
ms.date: 08/19/2019
helpviewer_keywords:
- public members
- source files
- MFC, source files
- MFC source files
- comments, MFC
- private member access
- protected member access
- source files, MFC
ms.assetid: 3230e8fb-3b69-4ddf-9538-365ac7ea5e72
ms.openlocfilehash: ca5799da7a6ada42db20e3551b3fb7262e8990a0
ms.sourcegitcommit: 9d4ffb8e6e0d70520a1e1a77805785878d445b8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/20/2019
ms.locfileid: "69631666"
---
# <a name="using-the-mfc-source-files"></a>Korzystanie z plików źródłowych MFC

Biblioteka Microsoft Foundation Class (MFC) oferuje pełny kod źródłowy. Pliki nagłówkowe (. h) znajdują się w katalogu *\atlmfc\include* . Pliki implementacji (. cpp) znajdują się w katalogu *\atlmfc\src\mfc* .

W tym artykule wyjaśniono konwencje używane przez MFC do komentowania różnych części każdej klasy, znaczenie tych komentarzy i informacje, które należy znaleźć w poszczególnych sekcjach. Kreatorzy programu Visual Studio używają podobnych Konwencji dla klas, które tworzy dla Ciebie, i prawdopodobnie te konwencje będą przydatne dla własnego kodu.

Być może znasz **publiczne**, **chronione**i **prywatne** C++ słowa kluczowe. W plikach nagłówkowych MFC każda klasa może zawierać kilka z nich. Na przykład publiczne zmienne składowe i funkcje mogą znajdować się w więcej niż jednym **publicznym** słowie kluczowym. Jest to spowodowane tym, że MFC oddziela zmienne składowe i funkcje na podstawie ich użycia, a nie typu dostępu, który jest dozwolony. MFC zużywa oszczędne różnice. Nawet elementy uznawane za szczegóły implementacji są często **chronione**i wiele razy są **publiczne**. Chociaż dostęp do szczegółów implementacji nie jest odradzany, MFC nie opuszcza tej decyzji.

Zarówno w przypadku plików źródłowych MFC, jak i plików nagłówkowych tworzonych przez Kreatora aplikacji MFC, znajdziesz Komentarze takie jak te, które znajdują się w deklaracjach klas (zwykle w tej kolejności):

`// Constructors`

`// Attributes`

`// Operations`

`// Overridables`

`// Implementation`

## <a name="an-example-of-the-comments"></a>Przykład komentarzy

W poniższej częściowej liście klas `CStdioFile` użyto większości standardowych komentarzy, które MFC wykorzystują w swoich klasach, aby podzielić elementy członkowskie klasy na używane sposoby:

```cpp
/*============================================================================*/
// STDIO file implementation

class CStdioFile : public CFile
{
    DECLARE_DYNAMIC(CStdioFile)

public:
// Constructors
    CStdioFile();

    // . . .

// Attributes
    FILE* m_pStream;    // stdio FILE
                        // m_hFile from base class is _fileno(m_pStream)

// Operations
    // reading and writing strings
    virtual void WriteString(LPCTSTR lpsz);
    virtual LPTSTR ReadString(_Out_writes_z_(nMax) LPTSTR lpsz, _In_ UINT nMax);
    virtual BOOL ReadString(CString& rString);

// Implementation
public:
    virtual ~CStdioFile();
#ifdef _DEBUG
    void Dump(CDumpContext& dc) const;
#endif
    virtual ULONGLONG GetPosition() const;
    virtual ULONGLONG GetLength() const;
    virtual BOOL Open(LPCTSTR lpszFileName, UINT nOpenFlags, CFileException* pError = NULL);

    // . . .

protected:
    void CommonBaseInit(FILE* pOpenStream, CAtlTransactionManager* pTM);
    void CommonInit(LPCTSTR lpszFileName, UINT nOpenFlags, CAtlTransactionManager* pTM);
};
```

Te komentarze są jednolicie oznaczane sekcjami deklaracji klasy, które zawierają podobne rodzaje elementów członkowskich klasy. Pamiętaj, że są to konwencje MFC, nie ustawiaj reguł.

## <a name="-constructors-comment"></a>Komentarz dotyczący konstruktorów

Sekcja deklaracji klasy MFC deklaruje konstruktory (w C++ sensie) i wszelkie funkcje inicjujące wymagane do użycia obiektu. `// Constructors` Na przykład, `CWnd::Create` znajduje się w sekcji konstruktory, ponieważ przed `CWnd` użyciem obiektu, musi to być "w pełni skonstruowane" przez pierwsze wywołanie C++ konstruktora, a następnie wywołanie `Create` funkcji. Zazwyczaj te elementy członkowskie są publiczne.

Na przykład Klasa `CStdioFile` ma pięć konstruktorów, z których jedna jest wyświetlana na liście w ramach [przykładu komentarzy](#an-example-of-the-comments).

## <a name="-attributes-comment"></a>Komentarz dotyczący atrybutów

`// Attributes` Sekcja deklaracji klasy MFC zawiera atrybuty publiczne (lub właściwości) obiektu. Zazwyczaj atrybuty są zmiennymi składowymi lub pobieraniem/ustawianiem funkcji. Funkcje "Get" i "Set" mogą nie być wirtualne. Funkcje "Get" często są **stałe**, ponieważ w większości przypadków nie mają one efektów ubocznych. Te elementy członkowskie są zwykle publiczne. Atrybuty chronione i prywatne zwykle znajdują się w sekcji implementacji.

W przykładowej liście z klasy `CStdioFile`, w [przykładzie komentarzy](#an-example-of-the-comments), lista zawiera jedną zmienną członkowską, *m_pStream*. `CDC` Wyświetla listę niemal 20 członków poniżej tego komentarza.

> [!NOTE]
> Duże klasy, takie jak `CDC` i `CWnd`, mogą mieć wiele elementów członkowskich, które po prostu wyświetlają wszystkie atrybuty w jednej grupie, nie dodawaj znacznie do przejrzystości. W takich przypadkach Biblioteka klas używa innych komentarzy jako nagłówków, aby dodatkowo odróżnić członków. Na przykład `CDC` używa `// Device-Context Functions`, `// Drawing Tool Functions`, inietylko.`// Drawing Attribute Functions` Grupy reprezentujące atrybuty będą zgodne z normalną składnią opisaną powyżej. Wiele klas OLE ma sekcję implementacji o nazwie `// Interface Maps`.

## <a name="-operations-comment"></a>Komentarz do operacji

`// Operations` Sekcja deklaracji klasy MFC zawiera funkcje składowe, które można wywołać na obiekcie, aby wykonać czynności lub wykonać akcje (wykonaj operacje). Te funkcje zwykle nie są**stałe** , ponieważ zazwyczaj mają efekty uboczne. Mogą być wirtualne lub niewirtualne w zależności od potrzeb klasy. Zazwyczaj te elementy członkowskie są publiczne.

W przykładowej liście z klasy `CStdioFile`, w [przykładzie komentarzy](#an-example-of-the-comments), lista zawiera trzy funkcje składowe w ramach tego komentarza: `WriteString` i dwa przeciążenia. `ReadString`

Podobnie jak w przypadku atrybutów, operacje można poddzielić dalej.

## <a name="-overridables-comment"></a>Komentarz dotyczący zażądanych

`// Overridables` Sekcja deklaracji klasy MFC zawiera funkcje wirtualne, które można przesłonić w klasie pochodnej, gdy trzeba zmodyfikować zachowanie klasy bazowej. Są one zwykle nazywane rozpoczynaniem się od "on", chociaż nie jest to absolutnie konieczne. W tym miejscu funkcje są przeznaczone do przesłaniania i często implementują lub dostarczają różnego rodzaju "wywołanie zwrotne" lub "hak". Zazwyczaj te elementy członkowskie są chronione.

W samej MFC, czyste funkcje wirtualne są zawsze umieszczane w tej sekcji. Czysta funkcja wirtualna w C++ programie przyjmuje postać:

`virtual void OnDraw( ) = 0;`

W przykładowej liście z klasy `CStdioFile`, w [przykładzie komentarzy](#an-example-of-the-comments), lista nie zawiera żadnych zażądanych sekcji. `CDocument`Z drugiej strony, zawiera listę około 10 zażądanych funkcji Członkowskich.

W niektórych klasach można również zobaczyć komentarz `// Advanced Overridables`. Te funkcje to te, które tylko zaawansowani programiści powinni próbować przesłonić. Prawdopodobnie nigdy nie musisz go przesłonić.

> [!NOTE]
> Konwencje opisane w tym artykule również działają prawidłowo, ogólnie w przypadku automatyzacji (dawniej znanych jako Automatyzacja OLE) metod i właściwości. Metody automatyzacji przypominają operacje MFC. Właściwości automatyzacji są podobne do atrybutów MFC. Zdarzenia automatyzacji (obsługiwane przez kontrolki ActiveX, znane wcześniej jako formanty OLE) są podobne do funkcji składowych MFC.

## <a name="-implementation-comment"></a>Komentarz dotyczący implementacji

`// Implementation` Sekcja jest najważniejszym elementem każdej deklaracji klasy MFC.

W tej sekcji omówiono wszystkie szczegóły implementacji. W tej sekcji mogą występować zarówno zmienne Członkowskie, jak i funkcje członkowskie. Wszystko, co znajduje się poniżej tego wiersza, może ulec zmianie w przyszłych wersjach MFC. Chyba że nie można tego uniknąć, nie należy polegać na szczegółach poniżej `// Implementation` wiersza. Ponadto elementy członkowskie zadeklarowane poniżej wiersza implementacji są nieudokumentowane, mimo że niektóre implementacje zostały omówione w uwagach technicznych. Zastąpienia funkcji wirtualnych w klasie podstawowej znajdują się w tej sekcji, niezależnie od tej, która sekcja jest zdefiniowana w. Gdy funkcja zastępuje implementację klasy bazowej, jest traktowana jako szczegóły implementacji. Zazwyczaj te elementy członkowskie są chronione, ale nie zawsze.

`// Implementation` [](#an-example-of-the-comments)Na liście pod przykładem komentarzy elementy członkowskie zadeklarowane poniżej komentarza mogą być deklarowane jako publiczne, chronione lub prywatne. `CStdioFile` Używaj tych członków tylko z zachowaniem ostrożności, ponieważ mogą one ulec zmianie w przyszłości. Aby implementacja biblioteki klas działała prawidłowo, może być konieczne zadeklarowanie grupy członków jako **publicznej** . Nie oznacza to jednak, że Licencjobiorca może bezpiecznie używać elementów członkowskich, tak jak zostało zadeklarowane.

> [!NOTE]
> Komentarze do pozostałych typów mogą znajdować się powyżej lub poniżej `// Implementation` komentarza. W obu przypadkach opisują rodzaje członków zadeklarowanych poniżej. Jeśli występują one poniżej `// Implementation` komentarza, należy zastanowić się, że elementy członkowskie mogą ulec zmianie w przyszłych wersjach MFC.

## <a name="see-also"></a>Zobacz także

[Tematy ogólne dotyczące MFC](../mfc/general-mfc-topics.md)
