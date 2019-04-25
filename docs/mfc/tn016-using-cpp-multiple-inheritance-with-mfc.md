---
title: 'TN016: Używanie dziedziczenia wielokrotnego języka C++ z MFC'
ms.date: 06/28/2018
f1_keywords:
- vc.inheritance
helpviewer_keywords:
- TN016
- MI (Multiple Inheritance)
- multiple inheritance, MFC support for
ms.assetid: 4ee27ae1-1410-43a5-b111-b6af9b84535d
ms.openlocfilehash: 76dc2e856ca7db783ee542aa2dbb498fd4c1a769
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62306132"
---
# <a name="tn016-using-c-multiple-inheritance-with-mfc"></a>TN016: Używanie dziedziczenia wielokrotnego języka C++ z MFC

Ta uwaga opisuje sposób dziedziczenie wielokrotne (MI) za pomocą klasy Microsoft Foundation. Korzystanie z wystąpienia Zarządzanego nie jest wymagana z MFC. Warstwa nie jest używany w żadnych klas MFC i nie jest wymagana do zapisywania biblioteki klas.

Następujące tematy podrzędne opisują, jak MI wpływa na korzystanie z typowych idiomy MFC, a także zasłaniania ograniczeń MI. Niektóre z tych ograniczeń są ogólne ograniczenia dotyczące języka C++. Inne są nakładane przez architekturę MFC.

Na koniec ta uwaga techniczna znajduje się kompletna aplikacja MFC, która używa aparatu MI.

## <a name="cruntimeclass"></a>CRuntimeClass

Trwałość i mechanizmów tworzenia obiekt dynamiczny użytkowania MFC [CRuntimeClass](../mfc/reference/cruntimeclass-structure.md) struktury danych, aby jednoznacznie zidentyfikować klasy. MFC kojarzy jedną z tych struktur do każdej klasy dynamiczne i/lub możliwe do serializacji w aplikacji. Te struktury są inicjowane podczas uruchamiania aplikacji przy użyciu specjalnych obiektu statycznego typu `AFX_CLASSINIT`.

Bieżąca implementacja parametru `CRuntimeClass` nie obsługuje informacje o typie środowiska uruchomieniowego MI. Oznacza to, że wystąpienia Zarządzanego nie można używać w aplikacji MFC. Jednak masz określone obowiązki podczas pracy z obiektami, które mają więcej niż jednej klasy bazowej.

[CObject::IsKindOf](../mfc/reference/cobject-class.md#iskindof) metody nie poprawnie określi typ obiektu, jeśli ma on wiele klas podstawowych. W związku z tym, nie można użyć [CObject](../mfc/reference/cobject-class.md) jako wirtualnej klasy bazowej, a wszystkie wywołania do `CObject` takich jak funkcje Członkowskie [CObject::Serialize](../mfc/reference/cobject-class.md#serialize) i [NoweCObject::operator](../mfc/reference/cobject-class.md#operator_new)musi mieć zakres kwalifikatorów, tak że C++ mogą rozróżniania wywołań funkcji odpowiednie. Jeśli program używa MI w MFC, klasę zawierającą `CObject` klasa bazowa musi być klasy skrajnie po lewej na liście klas bazowych.

Alternatywą jest użycie `dynamic_cast` operatora. Rzutowanie obiektu z MI do jednej z jej klas podstawowych będzie wymusić na kompilatorze funkcji w podanej klasy bazowej. Aby uzyskać więcej informacji, zobacz [dynamic_cast Operator](../cpp/dynamic-cast-operator.md).

## <a name="cobject---the-root-of-all-classes"></a>CObject — głównego wszystkie klasy

Wszystkie klasy znaczące pochodzi bezpośrednio lub pośrednio z klasy `CObject`. `CObject` jest nie zawiera żadnych danych elementu członkowskiego, ale niesie ze sobą pewne funkcje domyślne. Gdy używasz wystąpienia Zarządzanego, zazwyczaj będzie dziedziczyć z co najmniej dwóch `CObject`-klas pochodnych. W poniższym przykładzie pokazano, jak klasy mogą dziedziczyć [CFrameWnd](../mfc/reference/cframewnd-class.md) i [CObList](../mfc/reference/coblist-class.md):

```cpp
class CListWnd : public CFrameWnd, public CObList
{
    // ...
};
CListWnd myListWnd;
```

W tym przypadku `CObject` znajduje się, że dwa razy. Oznacza to konieczność sposób odróżnić wszystkich odwołań do `CObject` metody lub operatorów. **Nowy operator** i [operatora delete](../mfc/reference/cobject-class.md#operator_delete) są dwa operatory, które muszą być rozróżniane. Inny przykład poniższy kod powoduje błąd w czasie kompilacji:

```cpp
myListWnd.Dump(afxDump); // compile time error, CFrameWnd::Dump or CObList::Dump
```

## <a name="reimplementing-cobject-methods"></a>Reimplementing metod obiektu CObject

Podczas tworzenia nowej klasy ma co najmniej dwóch `CObject` pochodnych klas bazowych, należy ponownie `CObject` metody, które chcesz, aby inne osoby do użycia. Operatory **nowe** i **Usuń** są obowiązkowe i [zrzutu](../mfc/reference/cobject-class.md#dump) jest zalecane. Następujące reimplements przykład **nowe** i **Usuń** operatorów i `Dump` metody:

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

## <a name="virtual-inheritance-of-cobject"></a>Dziedziczenie wirtualne z obiektu CObject

Może wydawać się, że praktycznie dziedziczenie `CObject` może rozwiązać problem niejednoznaczności funkcji, ale nie jest wymagane. Ponieważ nie ma żadnych danych elementu członkowskiego w `CObject`, nie trzeba dziedziczenie wirtualne, aby zapobiec wielu kopii danych elementu członkowskiego klasy bazowej. W pierwszym przykładzie, pokazaną wcześniej `Dump` metoda wirtualna jest nadal niejednoznaczny, ponieważ jest implementowane w inny sposób w `CFrameWnd` i `CObList`. Najlepszym sposobem, aby usunąć niejednoznaczność jest postępuj zgodnie z zaleceniami znajdujące się w poprzedniej sekcji.

## <a name="cobjectiskindof-and-run-time-typing"></a>CObject::IsKindOf i wpisując Run-Time

Mechanizm Pisownia środowiska wykonawczego, obsługiwane przez MFC w `CObject` używa makra DECLARE_DYNAMIC, IMPLEMENT_DYNAMIC, DECLARE_DYNCREATE, IMPLEMENT_DYNCREATE DECLARE_SERIAL i IMPLEMENT_SERIAL. Te makra można wykonywać sprawdzanie typu run-time w celu zagwarantowania bezpiecznej rzutowań.

Te makra obsługują tylko pojedyncza klasa bazowa i będzie działać w sposób ograniczony do klasy wielokrotnie dziedziczone. Klasy bazowej, którą określisz w IMPLEMENT_DYNAMIC lub IMPLEMENT_SERIAL powinny być klasą bazową pierwszy (lub najbardziej z lewej strony). Ta umieszczania umożliwi kontrola skrajnej lewej klasy podstawowej tylko typów. System typu run-time będzie wiadomo, nie ma dodatkowych klas bazowych. W poniższym przykładzie systemów wykonawczej będzie wykonywać sprawdzenie względem typu `CFrameWnd`, ale będzie nic wiedzieć o `CObList`.

```cpp
class CListWnd : public CFrameWnd, public CObList
{
    DECLARE_DYNAMIC(CListWnd)
    // ...
};
IMPLEMENT_DYNAMIC(CListWnd, CFrameWnd)
```

## <a name="cwnd-and-message-maps"></a>CWnd i mapy komunikatów

Działają poprawnie, w systemie mapy komunikatów MFC są dwoma dodatkowymi wymaganiami:

- Musi istnieć tylko jeden `CWnd`-pochodzi z klasy bazowej.

- `CWnd`-Klasy pochodnej musi być klasą bazową pierwszy (lub najbardziej z lewej strony).

Poniżej przedstawiono kilka przykładów, które nie będą działać:

```cpp
class CTwoWindows : public CFrameWnd, public CEdit
{ /* ... */ }; // error : two copies of CWnd

class CListEdit : public CObList, public CEdit
{ /* ... */ }; // error : CEdit (derived from CWnd) must be first
```

## <a name="a-sample-program-using-mi"></a>Przykładowy Program za pomocą wystąpienia Zarządzanego

Poniższy przykład to autonomiczna aplikacja, która składa się z jedną klasę pochodną `CFrameWnd` i [CWinApp](../mfc/reference/cwinapp-class.md). Firma Microsoft nie zaleca się struktury aplikacji w ten sposób, że jest to przykład najmniejszy aplikacji MFC, który ma jedną klasę.

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

[Uwagi techniczne według numerów](../mfc/technical-notes-by-number.md)<br/>
[Uwagi techniczne według kategorii](../mfc/technical-notes-by-category.md)
