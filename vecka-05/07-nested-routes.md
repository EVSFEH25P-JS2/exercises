# Nested routes (Utmaning)

## Mål

Öva på nested routes med index route och `Outlet`.

## Förkunskaper

- [React Router](../../documents/07-react-router.md)
- [Layout route](03-layout-route.md)

## Instruktioner

1. Utgå från en app som redan har en huvudlayout med navbar och `Outlet` (från övning 03).
2. Skapa en dashboard-sektion med tre nested routes:
   - `/dashboard` → visar en översikt (index route)
   - `/dashboard/profile` → visar profilinformation
   - `/dashboard/settings` → visar inställningar
3. Skapa en `DashboardLayout`-component med en sidebar-navigation (till vänster) och en `Outlet` (till höger).
4. Sidebar-navigationen ska ha `NavLink`:ar till alla tre dashboard-sidor med aktiv markering.
5. Nästla dashboard-routes inuti huvudlayouten så att header och footer fortfarande visas.
6. Lägg till en länk till `/dashboard` i huvudnavbaren.

## Förväntat resultat

En dashboard med en egen sidebar inuti huvudlayouten. Klick i sidebaren byter content utan att sidebaren eller huvudlayouten försvinner. Huvudlayoutens header och footer visas runt allt.

## Tips

<details>
<summary>Ledtråd 1</summary>

Routes nästlas så här:

```jsx
<Route element={<Layout />}>
  <Route path="/" element={<Home />} />
  <Route path="/dashboard" element={<DashboardLayout />}>
    <Route index element={<DashboardHome />} />
    <Route path="profile" element={<Profile />} />
    <Route path="settings" element={<Settings />} />
  </Route>
</Route>
```

Barn-routes under `/dashboard` behöver inte skriva `/dashboard/` — de ärver det automatiskt.

</details>

<details>
<summary>Ledtråd 2</summary>

`DashboardLayout` använder sin egen `Outlet`:

```jsx
function DashboardLayout() {
  return (
    <div style={{ display: "flex" }}>
      <nav>
        <NavLink to="/dashboard" end>Översikt</NavLink>
        <NavLink to="/dashboard/profile">Profil</NavLink>
        <NavLink to="/dashboard/settings">Inställningar</NavLink>
      </nav>
      <main>
        <Outlet />
      </main>
    </div>
  );
}
```

`end`-propen på första NavLink:en gör att den bara är aktiv på exakt `/dashboard`.

</details>
