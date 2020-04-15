---
title: Klasa CCriticalSection
ms.date: 11/04/2016
f1_keywords:
- CCriticalSection
- AFXMT/CCriticalSection
- AFXMT/CCriticalSection::CCriticalSection
- AFXMT/CCriticalSection::Lock
- AFXMT/CCriticalSection::Unlock
- AFXMT/CCriticalSection::m_sect
helpviewer_keywords:
- CCriticalSection [MFC], CCriticalSection
- CCriticalSection [MFC], Lock
- CCriticalSection [MFC], Unlock
- CCriticalSection [MFC], m_sect
ms.assetid: f776f74b-5b0b-4f32-9c13-2b8e4a0d7b2b
ms.openlocfilehash: d79199a332f6930619e6b4995b04bc590b6ea580
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369364"
---
# <a name="ccriticalsection-class"></a>Klasa CCriticalSection

Reprezentuje "sekcji krytycznej" — obiekt synchronizacji, który umożliwia jeden wątek naraz, aby uzyskać dostęp do zasobu lub sekcji kodu.

## <a name="syntax"></a>Składnia

```
class CCriticalSection : public CSyncObject
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CCriticalSekcja::CCriticalSekcja](#ccriticalsection)|Konstruuje `CCriticalSection` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CCriticalSekcja::Blokada](#lock)|Służy do uzyskiwania `CCriticalSection` dostępu do obiektu.|
|[CCriticalSection::Odblokuj](#unlock)|Zwalnia `CCriticalSection` obiekt.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CCriticalSekcja::operator CRITICAL_SECTION*](#operator_critical_section_star)|Pobiera wskaźnik do obiektu CRITICAL_SECTION wewnętrznej.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CCriticalSekcja::m_sect](#m_sect)|Obiekt CRITICAL_SECTION.|

## <a name="remarks"></a>Uwagi

Sekcje krytyczne są przydatne, gdy tylko jeden wątek naraz może być dozwolony do modyfikowania danych lub innego kontrolowanego zasobu. Na przykład dodawanie węzłów do połączonej listy jest procesem, który powinien być dozwolony tylko przez jeden wątek naraz. Za pomocą `CCriticalSection` obiektu do kontrolowania połączonej listy, tylko jeden wątek naraz może uzyskać dostęp do listy.

> [!NOTE]
> Funkcjonalność `CCriticalSection` klasy jest dostarczana przez rzeczywisty obiekt CRITICAL_SECTION Win32.

Sekcje krytyczne są używane zamiast muteksów (patrz [CMutex),](../../mfc/reference/cmutex-class.md)gdy szybkość jest krytyczna i zasób nie będzie używany przez granice procesu.

Istnieją dwie metody używania `CCriticalSection` obiektu: autonomiczne i osadzone w klasie.

- Metoda autonomiczna Aby użyć `CCriticalSection` obiektu autonomicznego, `CCriticalSection` skonstruuj obiekt, gdy jest potrzebny. Po pomyślnym powrocie z konstruktora jawnie zablokować obiekt za pomocą wywołania [Lock](#lock). Zadzwoń [odblokowuj](#unlock) po zakończeniu uzyskiwania dostępu do sekcji krytycznej. Ta metoda, podczas gdy jaśniejsze dla kogoś czytania kodu źródłowego, jest bardziej podatne na błędy, jak należy pamiętać, aby zablokować i odblokować sekcję krytyczną przed i po dostępie.

   Bardziej preferowaną metodą jest użycie [CSingleLock](../../mfc/reference/csinglelock-class.md) klasy. Ma również `Lock` i `Unlock` metody, ale nie musisz się martwić o odblokowanie zasobu, jeśli wystąpi wyjątek.

- Metoda osadzona Można również udostępnić klasę z `CCriticalSection`wieloma wątkami, dodając element członkowski danych typu do klasy i blokując element członkowski danych w razie potrzeby.

Aby uzyskać więcej `CCriticalSection` informacji na temat używania obiektów, zobacz artykuł [Wielowątkowość: Jak korzystać z klas synchronizacji](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[CSyncObject (100)](../../mfc/reference/csyncobject-class.md)

`CCriticalSection`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxmt.h

## <a name="ccriticalsectionccriticalsection"></a><a name="ccriticalsection"></a>CCriticalSekcja::CCriticalSekcja

Konstruuje `CCriticalSection` obiekt.

```
CCriticalSection();
```

### <a name="remarks"></a>Uwagi

Aby uzyskać dostęp `CCriticalSection` do obiektu lub zwolnić go, należy utworzyć obiekt [CSingleLock](../../mfc/reference/csinglelock-class.md) i wywołać jego funkcje członkowskie [Zablokuj](../../mfc/reference/csinglelock-class.md#lock) i [odblokowując.](../../mfc/reference/csinglelock-class.md#unlock) Jeśli `CCriticalSection` obiekt jest używany autonomicznie, [wywołać](#unlock) jego Unlock funkcji elementu członkowskiego, aby go zwolnić.

Jeśli konstruktor nie może przydzielić wymaganej pamięci systemowej, wyjątek pamięci (typu [CMemoryException)](../../mfc/reference/cmemoryexception-class.md)jest automatycznie generowany.

### <a name="example"></a>Przykład

  Zobacz przykład [ccriticalSection::Lock](#lock).

## <a name="ccriticalsectionlock"></a><a name="lock"></a>CCriticalSekcja::Blokada

Wywołanie tej funkcji elementu członkowskiego, aby uzyskać dostęp do obiektu sekcji krytycznej.

```
BOOL Lock();
BOOL Lock(DWORD dwTimeout);
```

### <a name="parameters"></a>Parametry

*dwTimeout*<br/>
`Lock`ignoruje tę wartość parametru.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli funkcja zakończyła się pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

`Lock`jest wywołaniem blokowania, które nie powróci, dopóki obiekt sekcji krytycznej nie zostanie zasygnalizowany (stanie się dostępny).

Jeśli czas oczekiwania są konieczne, można użyć [CMutex](../../mfc/reference/cmutex-class.md) obiektu `CCriticalSection` zamiast obiektu.

Jeśli `Lock` nie uda się przydzielić niezbędnej pamięci systemowej, wyjątek pamięci (typu [CMemoryException)](../../mfc/reference/cmemoryexception-class.md)jest automatycznie generowany.

### <a name="example"></a>Przykład

W tym przykładzie pokazano zagnieżdżone podejście sekcji krytycznej, kontrolując dostęp do zasobu udostępnionego (obiektu statycznego) `_strShared` przy użyciu obiektu udostępnionego. `CCriticalSection` Funkcja `SomeMethod` demonstruje aktualizowanie zasobu udostępnionego w bezpieczny sposób.

[!code-cpp[NVC_MFC_Utilities#11](../../mfc/codesnippet/cpp/ccriticalsection-class_1.h)]

## <a name="ccriticalsectionm_sect"></a><a name="m_sect"></a>CCriticalSekcja::m_sect

Zawiera obiekt sekcji krytycznej, `CCriticalSection` który jest używany przez wszystkie metody.

```
CRITICAL_SECTION m_sect;
```

## <a name="ccriticalsectionoperator-critical_section"></a><a name="operator_critical_section_star"></a>CCriticalSekcja::operator CRITICAL_SECTION*

Pobiera obiekt CRITICAL_SECTION.

```
operator CRITICAL_SECTION*();
```

### <a name="remarks"></a>Uwagi

Wywołanie tej funkcji, aby pobrać wskaźnik do wewnętrznego obiektu CRITICAL_SECTION.

## <a name="ccriticalsectionunlock"></a><a name="unlock"></a>CCriticalSection::Odblokuj

Zwalnia `CCriticalSection` obiekt do użycia przez inny wątek.

```
BOOL Unlock();
```

### <a name="return-value"></a>Wartość zwracana

Nonzero, `CCriticalSection` jeśli obiekt był własnością wątku i wydanie zakończyło się pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Jeśli `CCriticalSection` jest używany autonomiczny, `Unlock` musi być wywołana natychmiast po zakończeniu korzystania z zasobu kontrolowane przez sekcję krytyczną. Jeśli używany jest obiekt [CSingleLock,](../../mfc/reference/csinglelock-class.md) `CCriticalSection::Unlock` zostanie wywołany `Unlock` przez funkcję elementu członkowskiego obiektu lock.

### <a name="example"></a>Przykład

  Zobacz przykład [ccriticalSection::Lock](#lock).

## <a name="see-also"></a>Zobacz też

[Klasa CSyncObject](../../mfc/reference/csyncobject-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CMutex](../../mfc/reference/cmutex-class.md)
