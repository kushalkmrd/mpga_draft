---
layout: page
title: Issues Table
nav_order: 6
---

# Issues Table

Below is a dynamic table displaying the issues from our CSV data:

<table id="issuesTable" class="display">
    <thead>
        <tr>
            <th>Column1</th>
            <th>Column2</th>
            <!-- Add more headers as needed -->
        </tr>
    </thead>
    <tbody>
        <!-- Data will be populated by JavaScript -->
    </tbody>
</table>

<!-- Include jQuery and DataTables JS/CSS -->
<link rel="stylesheet" type="text/css" href="https://cdn.datatables.net/1.11.5/css/jquery.dataTables.css">
<script type="text/javascript" charset="utf8" src="https://code.jquery.com/jquery-3.6.0.min.js"></script>
<script type="text/javascript" charset="utf8" src="https://cdn.datatables.net/1.11.5/js/jquery.dataTables.js"></script>

<script type="text/javascript">
$(document).ready(function() {
    $.ajax({
        url: 'https://facilmap.org/sj19ktJypCpd/csv/24639',
        dataType: 'text',
    }).done(function(data) {
        var allRows = data.split(/\r?\n|\r/);
        var tableData = [];
        for (var singleRow = 1; singleRow < allRows.length; singleRow++) {
            var rowCells = allRows[singleRow].split(',');
            tableData.push(rowCells);
        }
        $('#issuesTable').DataTable({
            data: tableData,
            columns: [
                { title: "Column1" },
                { title: "Column2" }
                // Add more columns as needed
            ]
        });
    });
});
</script>