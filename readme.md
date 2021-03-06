<!-- default badges list -->
![](https://img.shields.io/endpoint?url=https://codecentral.devexpress.com/api/v1/VersionRange/431388567/21.1.5%2B)
[![](https://img.shields.io/badge/Open_in_DevExpress_Support_Center-FF7200?style=flat-square&logo=DevExpress&logoColor=white)](https://supportcenter.devexpress.com/ticket/details/T1047386)
[![](https://img.shields.io/badge/📖_How_to_use_DevExpress_Examples-e9f6fc?style=flat-square)](https://docs.devexpress.com/GeneralInformation/403183)
<!-- default badges end -->
# Dashboard for WinForms - How to Recalculate Totals When You Filter a Grid

The Dashboard does not fully support Grid column filters out of the box. These filters are used to select the data displayed in the Grid item. However, column filters do not affect total values calculated by the dashboard data engine. As a result, the Grid item shows filtered data when you apply grid column filters, but does not recalculate totals.

The example shows how to recalculate totals when you apply column filters to the Grid dashboard item.

> The example supports all the dashboard's [Total types](https://docs.devexpress.com/Dashboard/114794/winforms-dashboard/winforms-designer/create-dashboards-in-the-winforms-designer/dashboard-item-settings/grid/totals#totals-overview) except for "Auto". If you apply the "Auto" total type in the dashboard, "Not Supported" is shown instead of the total value.


## Example Overview

The example consists of the following classes:

### RecalculateGridTotalsModule

Implements the functionality to recalculate Grid totals. The [DashboardItemControlUpdated](https://docs.devexpress.com/Dashboard/DevExpress.DashboardWin.IDashboardControl.DashboardItemControlUpdated) event allows you to access the underlying `GridControl` object and change its options. The `GridView` column's [Summary](https://docs.devexpress.com/WindowsForms/DevExpress.XtraGrid.Columns.GridColumn.Summary) is used to modify column totals in the underlying UI control.

The example also updates total values when you export data. The [CustomExport](https://docs.devexpress.com/Dashboard/DevExpress.DashboardWin.IDashboardControl.CustomExport) event handler overrides the export procedure.

The module has the `Attach` and `Detach` public methods that allow you to execute the binding and unbinding code. 

* `Attach`

    Attaches the `Dashboard Designer` or `Dashboard Viewer` control and subscribes the [DashboardItemControlUpdated](https://docs.devexpress.com/Dashboard/DevExpress.DashboardWin.IDashboardControl.DashboardItemControlUpdated) and [CustomExport](https://docs.devexpress.com/Dashboard/DevExpress.DashboardWin.IDashboardControl.CustomExport) events.

* `Detach`

    Detaches the `Dashboard Designer` or `Dashboard Viewer` control and unsubscribes the `DashboardItemControlUpdated` and `CustomExport` events.

### Helper Classes

* `DashboardTotalsHelper` 

    Gets the total type of the underlying Grid Control based on the total type of the Dashboard Grid item.

* `FormatHelper` 

    Uses the formatting settings of dashboard's data items to format total values. 

<!-- default file list -->
## Files to Look At

* [RecalculateGridTotalsModule.cs](./CS/WinFormsDashboard_RecalculateTotals/Classes/RecalculateGridTotalsModule.cs) (VB: [RecalculateGridTotalsModule.vb](./VB/WinFormsDashboard_RecalculateTotals/Classes/RecalculateGridTotalsModule.vb))
* [DashboardTotalsHelper.cs](./CS/WinFormsDashboard_RecalculateTotals/Classes/DashboardTotalsHelper.cs) (VB: [DashboardTotalsHelper.vb](./VB/WinFormsDashboard_RecalculateTotals/Classes/DashboardTotalsHelper.vb))
* [FormatHelper.cs](./CS/WinFormsDashboard_RecalculateTotals/Classes/FormatHelper.cs) (VB: [FormatHelper.vb](./VB/WinFormsDashboard_RecalculateTotals/Classes/FormatHelper.vb))
* [DesignerForm1.cs](./CS/WinFormsDashboard_RecalculateTotals/DesignerForm1.cs) (VB: [DesignerForm1.vb](./VB/WinFormsDashboard_RecalculateTotals/DesignerForm1.vb))

<!-- default file list end -->

## Documentation

* [Totals](https://docs.devexpress.com/Dashboard/114794/winforms-dashboard/winforms-designer/create-dashboards-in-the-winforms-designer/dashboard-item-settings/grid/totals)
* [Access to Underlying Controls](https://docs.devexpress.com/Dashboard/18019/winforms-dashboard/winforms-viewer/access-to-underlying-controls)

## More Examples

- [Dashboard for ASP.NET Core - How to Recalculate Totals when You Filter a Grid](https://github.com/DevExpress-Examples/asp-net-core-dashboard-recalculate-totals)
