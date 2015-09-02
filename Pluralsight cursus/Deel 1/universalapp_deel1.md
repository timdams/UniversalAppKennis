# Universal App
Acties te doen in Pluralsight cursus [Introduction to Building Universal Store Apps With C# and XAML]
(http://www.pluralsight.com/courses/building-universal-store-apps-csharp-xaml) 
## Deel 1: demo universal app
* Verplaats Mainpage.Xaml naar shared project
* Voeg usercontrol toe aan Windows Phone project
* Copy usercontrol naar Windows project (drag+drop)
* Pas in beide usercontrols iets aan zodat ze niet meer identiek zijn
* Voeg usercontrol toe in mainpage.xaml (vergeet xmlns referentie niet)
* Test applicatie in beide versie en merk het verschil op

### Opmerking
Beide applicaties kunnen tegelijkertijd via F5 gestart worden:
* Rechterklik op Solution
* Ga naar Startup Project (onder Common Properties) 
* Kies "Multiple startup projects"
* Zet als action "start" bij beide projecten.

##  Deel 2: conditional compilation

* Voeg appbar boven en onderaan mainpage toe. Bboven en onder grid in xaml voeg je volgende code toe:
```
<Page.TopAppBar>
        <AppBar>
            <StackPanel Height="300" Orientation="Horizontal" HorizontalAlignment="Stretch" Background="Pink"></StackPanel>
        </AppBar>
</Page.TopAppBar>
```
en
```
<Page.BottomAppBar>
        <CommandBar Background="Green">
            <AppBarButton Icon="Like" Label="Like"/>
            <AppBarButton Icon="Clock" Label="Navigate"></AppBarButton>
        </CommandBar>
</Page.BottomAppBar>
```
* Als je nu probeert te runnen zal de Windows Phone versie een Exception werpen.
* We gaan daarom met Conditional compilation werken en gebruiken daarvoor de Nuget Package "XCC"  (Xaml Conditional Compilation). 
* Voeg deze package toe aan de SOLUTION (niet de aparte projecten)
* Voeg volgende conditions toe bovenaan in Mainpage.xaml:
```
    xmlns:win="condition:WINDOWS_APP"
    xmlns:wp="condition:WINDOWS_PHONE_APP"
```
* Om te voorkomen dat Visual Studio begint te huilen voegen we win en wp toe aan de Ignorable:
```
 mc:Ignorable="d win wp"
```
* Wanneer we nu ```win:``` voor een control zetten dan zal enkel de windows applicatie deze xaml control gebruiken (daar WP geen AppBar heeft), als volgt:
```
<win:Page.TopAppBar>
        <AppBar>
            <StackPanel Height="300" Orientation="Horizontal" HorizontalAlignment="Stretch" Background="Pink"></StackPanel>
        </AppBar>
</win:Page.TopAppBar>
```
en
```
<Page.BottomAppBar>
        <CommandBar Background="Green">
            <AppBarButton Icon="Like" Label="Like"/>
            <wp:AppBarButton Icon="Upload" Label="Navigate"></AppBarButton>
        </CommandBar>
</Page.BottomAppBar>
```
Merk op dat we er ook voor zorgen dat het upload icoontje enkel zichtbaar is in de Windows Phone versie.

## Einde
[Sourcecode](sourcecodedeel1.zip)