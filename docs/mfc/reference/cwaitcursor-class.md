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
ms.openlocfilehash: dfeedad18b3ebcefedff446699f074c86037a4a3
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222878"
---
# <a name="cwaitcursor-class"></a>Klasa CWaitCursor

Zapewnia jednowierszowy sposób wyświetlania kursora oczekiwania, który jest zwykle wyświetlany jako klepsydra, podczas gdy wykonujesz długotrwałą operację.

## <a name="syntax"></a>Składnia

```
class CWaitCursor
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CWaitCursor::CWaitCursor](#cwaitcursor)|Konstruuje `CWaitCursor` obiekt i wyświetla kursor oczekiwania.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CWaitCursor:: Restore](#restore)|Przywraca kursor oczekiwania po jego zmianie.|

## <a name="remarks"></a>Uwagi

`CWaitCursor`nie ma klasy bazowej.

Dobre praktyki programistyczne dla systemu Windows wymagają wyświetlania kursora oczekiwania przy każdym wykonywaniu operacji, która trwa zauważalny okres.

Aby wyświetlić kursor oczekiwania, po prostu Zdefiniuj `CWaitCursor` zmienną przed kodem, który wykonuje długotrwałą operację. Konstruktor obiektu automatycznie powoduje wyświetlenie kursora oczekiwania.

Gdy obiekt wykracza poza zakres (na końcu bloku, w którym `CWaitCursor` jest zadeklarowany obiekt), jego destruktor ustawia kursor do poprzedniego kursora. Inaczej mówiąc, obiekt wykonuje automatyczne czyszczenie niezbędne.

> [!NOTE]
> Ze względu na sposób działania konstruktorów i destruktorów `CWaitCursor` obiekty są zawsze deklarowane jako zmienne lokalne — nigdy nie są one deklarowane jako zmienne globalne ani nie są przypisane do **`new`** .

Jeśli wykonujesz operację, która może spowodować zmianę kursora, na przykład wyświetlenie okna komunikatu lub okna dialogowego, wywołaj funkcję [Przywróć](#restore) składową, aby przywrócić kursor oczekiwania. Nie można wywoływać `Restore` nawet wtedy, gdy kursor oczekiwania jest aktualnie wyświetlany.

Innym sposobem wyświetlania kursora oczekiwania jest użycie kombinacji [CCmdTarget:: BeginWaitCursor](../../mfc/reference/ccmdtarget-class.md#beginwaitcursor), [CCmdTarget:: EndWaitCursor](../../mfc/reference/ccmdtarget-class.md#endwaitcursor)i prawdopodobnie [CCmdTarget:: RestoreWaitCursor](../../mfc/reference/ccmdtarget-class.md#restorewaitcursor). `CWaitCursor`Jest to jednak łatwiejsze w użyciu, ponieważ nie trzeba ustawiać kursora do poprzedniego kursora, gdy skończysz pracę z długotrwałą operacją.

> [!NOTE]
> Zestaw MFC ustawia i przywraca kursor przy użyciu funkcji wirtualnej [CWinApp::D owaitcursor](../../mfc/reference/cwinapp-class.md#dowaitcursor) . Można zastąpić tę funkcję, aby zapewnić zachowanie niestandardowe.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`CWaitCursor`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin. h

## <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#62](../../mfc/reference/codesnippet/cpp/cwaitcursor-class_1.cpp)]

## <a name="cwaitcursorcwaitcursor"></a><a name="cwaitcursor"></a>CWaitCursor::CWaitCursor

Aby wyświetlić kursor oczekiwania, należy po prostu zadeklarować `CWaitCursor` obiekt przed kodem, który wykonuje długotrwałą operację.

```
CWaitCursor();
```

### <a name="remarks"></a>Uwagi

Konstruktor automatycznie powoduje wyświetlenie kursora oczekiwania.

Gdy obiekt wykracza poza zakres (na końcu bloku, w którym `CWaitCursor` jest zadeklarowany obiekt), jego destruktor ustawia kursor do poprzedniego kursora. Inaczej mówiąc, obiekt wykonuje automatyczne czyszczenie niezbędne.

Można wykorzystać fakt, że destruktor jest wywoływany na końcu bloku (który może znajdować się przed końcem funkcji), aby uaktywnić kursor oczekiwania tylko w części funkcji. Ta technika jest pokazana w drugim przykładzie poniżej.

> [!NOTE]
> Ze względu na sposób działania konstruktorów i destruktorów `CWaitCursor` obiekty są zawsze deklarowane jako zmienne lokalne — nigdy nie są deklarowane jako zmienne globalne ani nie są przypisane do **`new`** .

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#63](../../mfc/reference/codesnippet/cpp/cwaitcursor-class_2.cpp)]

## <a name="cwaitcursorrestore"></a><a name="restore"></a>CWaitCursor:: Restore

Aby przywrócić kursor oczekiwania, Wywołaj tę funkcję po wykonaniu operacji, takiej jak wyświetlanie okna komunikatu lub okna dialogowego, które może zmienić kursor oczekiwania na inny kursor.

```cpp
void Restore();
```

### <a name="remarks"></a>Uwagi

Jest to możliwe do wywołania `Restore` nawet wtedy, gdy kursor oczekiwania jest aktualnie wyświetlany.

Jeśli zachodzi potrzeba przywrócenia kursora oczekiwania w funkcji innej niż ta, w której `CWaitCursor` obiekt jest zadeklarowany, można wywołać [CCmdTarget:: RestoreWaitCursor](../../mfc/reference/ccmdtarget-class.md#restorewaitcursor).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#64](../../mfc/reference/codesnippet/cpp/cwaitcursor-class_3.cpp)]

## <a name="see-also"></a>Zobacz także

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[CCmdTarget:: BeginWaitCursor](../../mfc/reference/ccmdtarget-class.md#beginwaitcursor)<br/>
[CCmdTarget:: EndWaitCursor](../../mfc/reference/ccmdtarget-class.md#endwaitcursor)<br/>
[CCmdTarget:: RestoreWaitCursor](../../mfc/reference/ccmdtarget-class.md#restorewaitcursor)<br/>
[CWinApp::D oWaitCursor](../../mfc/reference/cwinapp-class.md#dowaitcursor)<br/>
[Jak: zmienić wskaźnik myszy w aplikacji klasy Microsoft Foundation](https://go.microsoft.com/fwlink/p/?linkid=128044)
