---
title: Klasa CWaitCursor
ms.date: 11/04/2016
f1_keywords:
- CWaitCursor
- AFXWIN/CWaitCursor
- AFXWIN/CWaitCursor::CWaitCursor
- AFXWIN/CWaitCursor::Restore
helpviewer_keywords:
- CWaitCursor [MFC], CWaitCursor
- CWaitCursor [MFC], Restore
ms.assetid: 5dfae2ff-d7b6-4383-b0ad-91e0868c67b3
ms.openlocfilehash: 7ce81e62ec6498ad84349108b4c4a07090b17de5
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57287147"
---
# <a name="cwaitcursor-class"></a>Klasa CWaitCursor

Oferuje sposób jednowierszowy, aby pokazać kursor oczekiwania, który jest zwykle wyświetlany jako Klepsydra podczas wykonywania długotrwałej operacji.

## <a name="syntax"></a>Składnia

```
class CWaitCursor
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CWaitCursor::CWaitCursor](#cwaitcursor)|Konstruuje `CWaitCursor` obiektu i wyświetla kursor oczekiwania.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CWaitCursor::Restore](#restore)|Przywraca kursor oczekiwania, po jego zmianie.|

## <a name="remarks"></a>Uwagi

`CWaitCursor` nie ma klasy bazowej.

Windows dobre praktyki programowania wymagają Wyświetla kursor oczekiwania, gdy wykonujesz operację, która przyjmuje zauważalne ilość czasu.

Aby wyświetlić kursor oczekiwania, wystarczy zdefiniować `CWaitCursor` zmiennej przed uruchomieniem kodu, który wykonuje długotrwałej operacji. Konstruktor obiektu automatycznie powoduje, że kursor oczekiwania, które mają być wyświetlane.

Gdy obiekt wykracza poza zakres (na końcu bloku, w którym `CWaitCursor` obiekt nie został zadeklarowany), jego destruktor ustawia kursor do poprzedniego kursora. Innymi słowy obiekt wykonuje niezbędne czyszczenia automatycznie.

> [!NOTE]
>  Ze względu na ich konstruktory i destruktory działania `CWaitCursor` obiektów zawsze są deklarowane jako zmienne lokalne — nigdy nie są one zadeklarowane jako zmienne globalne nie są one przydzielane za pomocą **nowe**.

Jeśli wykonujesz operację, co może prowadzić do kursora, które ma zostać zmieniony, takich jak wyświetlanie okna komunikatu lub okno dialogowe, wywołania [przywrócić](#restore) funkcja elementu członkowskiego, aby przywrócić kursor oczekiwania. Można wywołać `Restore` nawet gdy kursor oczekiwania jest aktualnie wyświetlany.

Innym sposobem wyświetlenia kursor oczekiwania jest użycie kombinacji [CCmdTarget::BeginWaitCursor](../../mfc/reference/ccmdtarget-class.md#beginwaitcursor), [CCmdTarget::EndWaitCursor](../../mfc/reference/ccmdtarget-class.md#endwaitcursor)i być może [CCmdTarget::RestoreWaitCursor](../../mfc/reference/ccmdtarget-class.md#restorewaitcursor). Jednak `CWaitCursor` jest łatwiejszy w obsłudze, ponieważ nie ma potrzeby ustaw kursor do poprzedniego kursora, po zakończeniu korzystania z długotrwałej operacji.

> [!NOTE]
>  Ustawia MFC i przywraca za pomocą kursora [CWinApp::DoWaitCursor](../../mfc/reference/cwinapp-class.md#dowaitcursor) funkcję wirtualną. Można zastąpić tę funkcję, aby zapewnić zachowanie niestandardowe.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`CWaitCursor`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin.h

## <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#62](../../mfc/reference/codesnippet/cpp/cwaitcursor-class_1.cpp)]

##  <a name="cwaitcursor"></a>  CWaitCursor::CWaitCursor

Aby wyświetlić kursor oczekiwania, po prostu zadeklarować `CWaitCursor` obiektu przed kod, który wykonuje długotrwałej operacji.

```
CWaitCursor();
```

### <a name="remarks"></a>Uwagi

Konstruktor automatycznie powoduje, że kursor oczekiwania, które mają być wyświetlane.

Gdy obiekt wykracza poza zakres (na końcu bloku, w którym `CWaitCursor` obiekt nie został zadeklarowany), jego destruktor ustawia kursor do poprzedniego kursora. Innymi słowy obiekt wykonuje niezbędne czyszczenia automatycznie.

Możesz korzystać z zalet fakt, że destruktor jest wywoływany pod koniec bloku, (które mogą się przed zakończeniem funkcji) aby uaktywnić kursor oczekiwania tylko część funkcji. Ta technika jest wyświetlany w drugim przykładzie poniżej.

> [!NOTE]
>  Ze względu na ich konstruktory i destruktory działania `CWaitCursor` obiektów zawsze są deklarowane jako zmienne lokalne — nigdy nie są one zadeklarowane jako zmienne globalne, ani nie są one przydzielane za pomocą **nowe**.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#63](../../mfc/reference/codesnippet/cpp/cwaitcursor-class_2.cpp)]

##  <a name="restore"></a>  CWaitCursor::Restore

Aby przywrócić kursor oczekiwania, wywołaj tę funkcję po wykonaniu operacji, takich jak wyświetlanie okna komunikatu lub okno dialogowe, które mogą ulec zmianie kursor oczekiwania na inny kursor.

```
void Restore();
```

### <a name="remarks"></a>Uwagi

Zgadzam się na wywołanie `Restore` nawet gdy kursor oczekiwania jest aktualnie wyświetlany.

Jeśli trzeba przywrócić kursor oczekiwania, który znajduje się w funkcji innych niż ten, w którym `CWaitCursor` obiekt nie został zadeklarowany, można wywołać [CCmdTarget::RestoreWaitCursor](../../mfc/reference/ccmdtarget-class.md#restorewaitcursor).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#64](../../mfc/reference/codesnippet/cpp/cwaitcursor-class_3.cpp)]

## <a name="see-also"></a>Zobacz także

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[CCmdTarget::BeginWaitCursor](../../mfc/reference/ccmdtarget-class.md#beginwaitcursor)<br/>
[CCmdTarget::EndWaitCursor](../../mfc/reference/ccmdtarget-class.md#endwaitcursor)<br/>
[CCmdTarget::RestoreWaitCursor](../../mfc/reference/ccmdtarget-class.md#restorewaitcursor)<br/>
[CWinApp::DoWaitCursor](../../mfc/reference/cwinapp-class.md#dowaitcursor)<br/>
[Jak mogę Zmień wskaźnik myszy w aplikacji klasy Microsoft Foundation](http://go.microsoft.com/fwlink/p/?linkid=128044)
