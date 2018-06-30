---
title: 'TN016: Używanie dziedziczenia wielokrotnego języka C++ z MFC | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 06/28/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.inheritance
dev_langs:
- C++
helpviewer_keywords:
- TN016
- MI (Multiple Inheritance)
- multiple inheritance, MFC support for
ms.assetid: 4ee27ae1-1410-43a5-b111-b6af9b84535d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 059e239f549f8da79207e5ff6a485643252d6d6b
ms.sourcegitcommit: 208d445fd7ea202de1d372d3f468e784e77bd666
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2018
ms.locfileid: "37123360"
---
# <a name="tn016-using-c-multiple-inheritance-with-mfc"></a>TN016: używanie dziedziczenia wielokrotnego języka C++ z MFC

Ta uwaga informacje dotyczące używania dziedziczenie wielokrotne (MI) z Microsoft Foundation Classes. Użycie MI nie jest wymagane w przypadku MFC. MI nie jest używany w żadnych klas MFC i nie jest wymagana do zapisania biblioteki klas.

Następujące tematy podrzędne opisują wpływ MI na użycie wspólnej MFC idioms, jak również obejmujące niektóre ograniczenia MI. Niektóre z tych ograniczeń są ograniczenia ogólne C++. Inne są nakładane przez architekturę MFC.

Na końcu tej uwagi techniczne można znaleźć pełnej aplikacji MFC, która używa MI.

## <a name="cruntimeclass"></a>CRuntimeClass

Trwałość i mechanizmów tworzenia obiekt dynamiczny użytkowania MFC [CRuntimeClass](../mfc/reference/cruntimeclass-structure.md) struktury danych do jednoznacznej identyfikacji klasy. MFC kojarzy jeden z tych struktur z każdej klasy dynamiczne i/lub do serializacji w aplikacji. Te struktury są inicjowane podczas uruchamiania aplikacji przy użyciu specjalnego obiektu statycznego typu `AFX_CLASSINIT`.

Bieżąca implementacja `CRuntimeClass` nie obsługuje informacji o typie środowiska uruchomieniowego MI. Oznacza to, że MI nie można użyć w aplikacji MFC. Użytkownik będzie jednak pewne obowiązki podczas pracy z obiektami, które mają więcej niż jedną klasę podstawową.

[CObject::IsKindOf](../mfc/reference/cobject-class.md#iskindof) — metoda będzie nie prawidłowo określić typ obiektu, jeśli ma ona wiele klas podstawowych. W związku z tym nie można użyć [CObject](../mfc/reference/cobject-class.md) jako wirtualna klasa podstawowa i wszystkie wywołania `CObject` takich jak funkcje Członkowskie [CObject::Serialize](../mfc/reference/cobject-class.md#serialize) i [NowyCObject::operator](../mfc/reference/cobject-class.md#operator_new)musi mieć zakres kwalifikatory, tak że C++ może odróżnienia wywołania funkcji odpowiednie. Gdy program użyje MI w MFC, klasa zawiera `CObject` klasy podstawowej musi być klasa lewej na liście klas podstawowych.

Alternatywą jest użycie `dynamic_cast` operatora. Rzutowanie obiektu z MI do jednej z jej klas podstawowych wymusi kompilator, aby użyć funkcji w podanej klasy podstawowej. Aby uzyskać więcej informacji, zobacz [dynamic_cast Operator](../cpp/dynamic-cast-operator.md).

## <a name="cobject---the-root-of-all-classes"></a>CObject — główny wszystkich klas

Wszystkie klasy znaczących pochodzi bezpośrednio lub pośrednio od klasy `CObject`. `CObject` jest nie zawiera żadnych danych elementu członkowskiego, ale ma niektóre funkcje domyślne. Gdy używasz MI można zwykle będzie dziedziczyć z co najmniej dwóch `CObject`-klas pochodnych. Poniższy przykład przedstawia, jak można dziedziczyć po klasie [cframewnd —](../mfc/reference/cframewnd-class.md) i [CObList](../mfc/reference/coblist-class.md):

```cpp
class CListWnd : public CFrameWnd, public CObList
{
    // ...
};
CListWnd myListWnd;
```

W takim przypadku `CObject` będzie dwa razy. Oznacza to, że konieczne sposób, aby odróżnić wszystkich odwołań do `CObject` metod lub operatorów. **Nowy operator** i [operatora delete](../mfc/reference/cobject-class.md#operator_delete) są dwa operatory, które muszą być rozróżniane. Inny przykład następujący kod powoduje błąd w czasie kompilacji:

```cpp
myListWnd.Dump(afxDump); // compile time error, CFrameWnd::Dump or CObList::Dump
```

## <a name="reimplementing-cobject-methods"></a>Reimplementing metody CObject

Podczas tworzenia nowej klasy ma co najmniej dwóch `CObject` podstawowej klas pochodnych powinny reimplement `CObject` metod, które mają inne osoby. Operatory **nowe** i **usunąć** są obowiązkowe i [zrzutu](../mfc/reference/cobject-class.md#dump) jest zalecane. Następujące reimplements przykład **nowe** i **usunąć** operatory i `Dump` metody:

```cpp
class CListWnd : public CFrameWnd, public CObList
{
public:
    void* operator new(size_t nSize)
    {
        return CFrameWnd:: operator new(nSize);
    }
    void operator delete(void* p)
    {
        CFrameWnd:: operator delete(p);
    }
    void Dump(CDumpContent& dc)
    {
        CFrameWnd::Dump(dc);
        CObList::Dump(dc);
    }
    // ...
};
```

## <a name="virtual-inheritance-of-cobject"></a>Wirtualnym dziedziczeniem CObject

Może wydawać się, że praktycznie dziedziczenie `CObject` może rozwiązać problem niejednoznaczności funkcji, ale nie jest uruchomiona. Ponieważ nie ma elementu członkowskiego danych w `CObject`, nie trzeba wirtualnego dziedziczenia, aby zapobiec wielu kopii danych elementu członkowskiego klasy podstawowej. W pierwszym przykładzie, która została przedstawiona wcześniej `Dump` metoda wirtualna jest nadal niejednoznaczne, ponieważ jest zaimplementowana w inny sposób `CFrameWnd` i `CObList`. Najlepszy sposób, aby usunąć niejednoznaczność jest postępować zgodnie z zaleceniami przedstawionych w poprzedniej sekcji.

## <a name="cobjectiskindof-and-run-time-typing"></a>CObject::IsKindOf i wpisując środowiska wykonawczego

Mechanizm pisania środowiska wykonawczego obsługiwane przez MFC w `CObject` korzysta z makra declare_dynamic —, implement_dynamic —, declare_dyncreate —, implement_dyncreate — declare_serial — i implement_serial —. Tych makr można przeprowadzić sprawdzania typu run-time zagwarantowanie downcasts bezpieczne.

Te makra obsługuje tylko pojedyncza klasa podstawowa i będzie działać w sposób ograniczony dla klasy mnożenie dziedziczone. Klasy podstawowej, które określisz w implement_dynamic — lub implement_serial — powinien być pierwszym (lub lewej) klasy podstawowej. Ta umieszczania umożliwi kontrola lewej klasy podstawowej tylko typów. System typu run-time będzie wiedział nic o dodatkowych klas podstawowych. W poniższym przykładzie wykona systemów czasu wykonywania typu sprawdzania przed `CFrameWnd`, ale znasz nic o `CObList`.

```cpp
class CListWnd : public CFrameWnd, public CObList
{
    DECLARE_DYNAMIC(CListWnd)
    // ...
};
IMPLEMENT_DYNAMIC(CListWnd, CFrameWnd)
```

## <a name="cwnd-and-message-maps"></a>CWnd i mapy komunikatów

Działał poprawnie, w systemie mapy komunikatów MFC są dwa dodatkowe wymagania:

- Musi istnieć tylko jedna `CWnd`-pochodzi z klasy podstawowej.

- `CWnd`— Podstawowy Klasa pochodna musi być klasą podstawową pierwszy (lub lewej).

Oto kilka przykładów, które nie będą działać:

```cpp
class CTwoWindows : public CFrameWnd, public CEdit
{ /* ... */ }; // error : two copies of CWnd

class CListEdit : public CObList, public CEdit
{ /* ... */ }; // error : CEdit (derived from CWnd) must be first
```

## <a name="a-sample-program-using-mi"></a>Przykładowy Program przy użyciu MI

Poniższy przykład jest autonomiczna aplikacja, która składa się z jedną klasę pochodną `CFrameWnd` i [CWinApp](../mfc/reference/cwinapp-class.md). Nie zaleca się struktury aplikacji w taki sposób, że jest to przykład najmniejszą aplikacji MFC, która zawiera jedną klasę.

```cpp
#include <afxwin.h>

class CHelloAppAndFrame : public CFrameWnd, public CWinApp
{
public:
    CHelloAppAndFrame() {}

    // Necessary because of MI disambiguity
    void* operator new(size_t nSize)
        { return CFrameWnd::operator new(nSize); }
    void operator delete(void* p)
        { CFrameWnd::operator delete(p); }

    // Implementation
    // CWinApp overrides
    virtual BOOL InitInstance();
    // CFrameWnd overrides
    virtual void PostNcDestroy();
    afx_msg void OnPaint();

    DECLARE_MESSAGE_MAP()
};

BEGIN_MESSAGE_MAP(CHelloAppAndFrame, CFrameWnd)
    ON_WM_PAINT()
END_MESSAGE_MAP()

// because the frame window is not allocated on the heap, we must
// override PostNCDestroy not to delete the frame object
void CHelloAppAndFrame::PostNcDestroy()
{
    // do nothing (do not call base class)
}

void CHelloAppAndFrame::OnPaint()
{
    CPaintDC dc(this);
    CRect rect;
    GetClientRect(rect);

    CString s = "Hello, Windows!";
    dc.SetTextAlign(TA_BASELINE | TA_CENTER);
    dc.SetTextColor(::GetSysColor(COLOR_WINDOWTEXT));
    dc.SetBkMode(TRANSPARENT);
    dc.TextOut(rect.right / 2, rect.bottom / 2, s);
}

// Application initialization
BOOL CHelloAppAndFrame::InitInstance()
{
    // first create the main frame
    if (!CFrameWnd::Create(NULL, "Multiple Inheritance Sample",
        WS_OVERLAPPEDWINDOW, rectDefault))
        return FALSE;

    // the application object is also a frame window
    m_pMainWnd = this;
    ShowWindow(m_nCmdShow);
    return TRUE;
}

CHelloAppAndFrame theHelloAppAndFrame;
```

## <a name="see-also"></a>Zobacz także

[Uwagi techniczne według numerów](../mfc/technical-notes-by-number.md)  
[Uwagi techniczne według kategorii](../mfc/technical-notes-by-category.md)  
