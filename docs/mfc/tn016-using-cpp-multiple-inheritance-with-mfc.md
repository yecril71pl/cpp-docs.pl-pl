---
title: 'TN016: używanie dziedziczenia wielokrotnego języka C++ z MFC'
ms.date: 06/28/2018
f1_keywords:
- vc.inheritance
helpviewer_keywords:
- TN016
- MI (Multiple Inheritance)
- multiple inheritance, MFC support for
ms.assetid: 4ee27ae1-1410-43a5-b111-b6af9b84535d
ms.openlocfilehash: c44639e713f6d0b26d5b74e9f645f60c8627e0c8
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87231770"
---
# <a name="tn016-using-c-multiple-inheritance-with-mfc"></a>TN016: używanie dziedziczenia wielokrotnego języka C++ z MFC

Ta Uwaga opisuje sposób używania wielu dziedziczeń (MI) z Microsoft Foundation Classes. Użycie elementu MI nie jest wymagane w przypadku MFC. Element MI nie jest używany w żadnej klasie MFC i nie jest wymagany do zapisu biblioteki klas.

W poniższych tematach opisano, jak to wpływa na użycie wspólnych idiomy MFC, jak również w przypadku niektórych ograniczeń. Niektóre z tych ograniczeń to ogólne ograniczenia języka C++. Inne są nakładane przez architekturę MFC.

Na końcu tej uwagi technicznej znajdziesz kompletną aplikację MFC, która używa MI.

## <a name="cruntimeclass"></a>CRuntimeClass

Mechanizmy trwałości i dynamicznego tworzenia obiektów MFC wykorzystują strukturę danych [CRuntimeClass](../mfc/reference/cruntimeclass-structure.md) do unikatowego identyfikowania klas. MFC kojarzy jedną z tych struktur z każdą dynamiczną i/lub możliwy do serializacji klasą w aplikacji. Te struktury są inicjowane, gdy aplikacja jest uruchamiana przy użyciu specjalnego obiektu statycznego typu `AFX_CLASSINIT` .

Bieżąca implementacja programu `CRuntimeClass` nie obsługuje informacji o typie środowiska uruchomieniowego mi. Nie oznacza to, że nie można użyć MI w aplikacji MFC. Jednak podczas pracy z obiektami, które mają więcej niż jedną klasę bazową, będziesz mieć pewne obowiązki.

Metoda [CObject:: IsKindOf](../mfc/reference/cobject-class.md#iskindof) nie będzie poprawnie określać typu obiektu, jeśli ma wiele klas bazowych. W związku z tym nie można użyć [CObject](../mfc/reference/cobject-class.md) jako wirtualnej klasy bazowej, a wszystkie wywołania `CObject` funkcji składowych, takich jak [CObject:: serializować](../mfc/reference/cobject-class.md#serialize) i [CObject:: operator new](../mfc/reference/cobject-class.md#operator_new) musi mieć kwalifikatory zakresu, aby C++ mogło odróżnić odpowiednie wywołanie funkcji. Gdy program używa elementu MI w MFC, Klasa, która zawiera `CObject` klasę bazową, musi być klasą znajdującą się po lewej stronie na liście klas bazowych.

Alternatywą jest użycie **`dynamic_cast`** operatora. Rzutowanie obiektu na jedną z jej klas podstawowych spowoduje wymuszenie użycia przez kompilator funkcji w podanej klasie bazowej. Aby uzyskać więcej informacji, zobacz [dynamic_cast operator](../cpp/dynamic-cast-operator.md).

## <a name="cobject---the-root-of-all-classes"></a>CObject — katalog główny wszystkich klas

Wszystkie znaczące klasy są wyprowadzane bezpośrednio lub pośrednio z klasy `CObject` . `CObject`nie ma żadnych danych elementu członkowskiego, ale ma pewne funkcje domyślne. Gdy używasz MI, zazwyczaj będzie dziedziczyć z dwóch lub więcej `CObject` klas pochodnych. Poniższy przykład ilustruje, jak Klasa może dziedziczyć z [obiektu CFrameWnd](../mfc/reference/cframewnd-class.md) i [CObList](../mfc/reference/coblist-class.md):

```cpp
class CListWnd : public CFrameWnd, public CObList
{
    // ...
};
CListWnd myListWnd;
```

W tym przypadku `CObject` jest uwzględniany dwa razy. Oznacza to, że konieczny jest sposób odróżnienia wszelkich odwołań do `CObject` metod lub operatorów. **Operator new** i [operator delete](../mfc/reference/cobject-class.md#operator_delete) to dwa operatory, które muszą być rozróżnienia. W innym przykładzie Poniższy kod powoduje błąd w czasie kompilacji:

```cpp
myListWnd.Dump(afxDump); // compile time error, CFrameWnd::Dump or CObList::Dump
```

## <a name="reimplementing-cobject-methods"></a>Zaimplementowanie metod CObject

Podczas tworzenia nowej klasy, która ma dwie lub więcej `CObject` pochodnych klas bazowych, należy ponownie wdrożyć metody, `CObject` które mają być używane przez inne osoby. Operatory **`new`** i **`delete`** są obowiązkowe, a [zrzut](../mfc/reference/cobject-class.md#dump) jest zalecany. Poniższy przykład umożliwia zaimplementowanie **`new`** operatorów i **`delete`** i `Dump` metody:

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

## <a name="virtual-inheritance-of-cobject"></a>Wirtualne dziedziczenie CObject

Może wydawać się, że wirtualna dziedziczenie `CObject` rozwiązało problem niejednoznaczności funkcji, ale nie jest to przypadek. Ponieważ nie ma żadnych danych elementu członkowskiego `CObject` , nie jest wymagane wirtualne dziedziczenie, aby uniemożliwić wiele kopii danych elementu członkowskiego klasy bazowej. W pierwszym przykładzie, który został pokazany wcześniej, `Dump` Metoda wirtualna jest nadal niejednoznaczna, ponieważ jest zaimplementowana inaczej w `CFrameWnd` i `CObList` . Najlepszym sposobem usunięcia niejednoznaczności jest przestrzeganie zaleceń przedstawionych w poprzedniej sekcji.

## <a name="cobjectiskindof-and-run-time-typing"></a>CObject:: IsKindOf i pisania w czasie wykonywania

Mechanizm wpisywania w czasie wykonywania obsługiwany przez MFC w programie `CObject` używa makr DECLARE_DYNAMIC, IMPLEMENT_DYNAMIC, DECLARE_DYNCREATE, IMPLEMENT_DYNCREATE, DECLARE_SERIAL i IMPLEMENT_SERIAL. Te makra mogą wykonywać sprawdzanie typu w czasie wykonywania, aby zagwarantować bezpieczną rzutowań.

Te makra obsługują tylko jedną klasę bazową i działają w ograniczony sposób w przypadku mnożenia dziedziczonych klas. Klasa bazowa określona w IMPLEMENT_DYNAMIC lub IMPLEMENT_SERIAL powinna być pierwszą klasą bazową (lub z lewej strony). To umieszczanie umożliwi przeprowadzenie sprawdzania typu tylko dla klasy podstawowej z lewej strony. System typu czasu wykonywania nie będzie niczego wiedzieć o dodatkowych klasach bazowych. W poniższym przykładzie systemy czasu wykonywania będą sprawdzać typ względem `CFrameWnd` , ale nic nie wie `CObList` .

```cpp
class CListWnd : public CFrameWnd, public CObList
{
    DECLARE_DYNAMIC(CListWnd)
    // ...
};
IMPLEMENT_DYNAMIC(CListWnd, CFrameWnd)
```

## <a name="cwnd-and-message-maps"></a>CWnd i mapy komunikatów

Aby system mapy komunikatów MFC działał prawidłowo, istnieją dwa dodatkowe wymagania:

- Musi istnieć tylko jedna `CWnd` pochodna Klasa bazowa.

- `CWnd`Pochodna Klasa bazowa musi być pierwszą (lub najbardziej do lewej) klasą bazową.

Oto kilka przykładów, które nie będą działały:

```cpp
class CTwoWindows : public CFrameWnd, public CEdit
{ /* ... */ }; // error : two copies of CWnd

class CListEdit : public CObList, public CEdit
{ /* ... */ }; // error : CEdit (derived from CWnd) must be first
```

## <a name="a-sample-program-using-mi"></a>Przykładowy program przy użyciu MI

Poniższy przykład jest aplikacją autonomiczną, która składa się z jednej klasy pochodnej od `CFrameWnd` i [CWinApp](../mfc/reference/cwinapp-class.md). Nie zalecamy struktury aplikacji w ten sposób, ale jest to przykład najmniejszej aplikacji MFC, która ma jedną klasę.

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

[Uwagi techniczne według numeru](../mfc/technical-notes-by-number.md)<br/>
[Uwagi techniczne według kategorii](../mfc/technical-notes-by-category.md)
