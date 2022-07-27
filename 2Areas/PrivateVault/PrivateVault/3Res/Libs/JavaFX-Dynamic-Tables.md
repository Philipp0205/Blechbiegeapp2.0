---
tags: programming, java, javafx, stackoverflow
---
Source: https://stackoverflow.com/questions/37559584/how-to-add-dynamic-columns-and-rows-to-tableview-in-java-fxml

---
What you are missing is a [cellValueFactory](https://docs.oracle.com/javase/8/javafx/api/javafx/scene/control/TableColumn.html#setCellValueFactory-javafx.util.Callback-) for your columns that will tell the column what value to display in its cells.

Something like this:

```java
TableView<ObservableList<String>> tableView = new TableView<>();
List<String> columnNames = dataGenerator.getNext(N_COLS);
for (int i = 0; i < columnNames.size(); i++) {
    final int finalIdx = i;
    TableColumn<ObservableList<String>, String> column = new TableColumn<>(
            columnNames.get(i)
    );
    column.setCellValueFactory(param ->
            new ReadOnlyObjectWrapper<>(param.getValue().get(finalIdx))
    );
    tableView.getColumns().add(column);
}
```

**Sample Application**

This solution was based slightly on Narayan's blog post: [Updated: Dynamic TableView Data From Database](http://blog.ngopal.com.np/2011/10/19/dyanmic-tableview-data-from-database/). Rather than that blog post, this solution uses a test data generator to generate some dummy data and some of the Java 8 lambda features which make the cell value factory definition a bit less unwieldy to write and look at.

[![fix off by one error](https://i.stack.imgur.com/pU9zv.png)](https://i.stack.imgur.com/pU9zv.png)

```java
import javafx.application.Application;
import javafx.beans.property.ReadOnlyObjectWrapper;
import javafx.collections.*;
import javafx.scene.Scene;
import javafx.scene.control.*;
import javafx.stage.Stage;

import java.util.*;

public class DynamicTableView extends Application {    
    private static final int N_COLS = 5;
    private static final int N_ROWS = 1_000;

    public void start(Stage stage) throws Exception {
        TestDataGenerator dataGenerator = new TestDataGenerator();

        TableView<ObservableList<String>> tableView = new TableView<>();

        // add columns
        List<String> columnNames = dataGenerator.getNext(N_COLS);
        for (int i = 0; i < columnNames.size(); i++) {
            final int finalIdx = i;
            TableColumn<ObservableList<String>, String> column = new TableColumn<>(
                    columnNames.get(i)
            );
            column.setCellValueFactory(param ->
                    new ReadOnlyObjectWrapper<>(param.getValue().get(finalIdx))
            );
            tableView.getColumns().add(column);
        }

        // add data
        for (int i = 0; i < N_ROWS; i++) {
            tableView.getItems().add(
                    FXCollections.observableArrayList(
                            dataGenerator.getNext(N_COLS)
                    )
            );
        }

        tableView.setPrefHeight(200);

        Scene scene = new Scene(tableView);
        stage.setScene(scene);
        stage.show();
    }

    public static void main(String[] args) {
        launch(args);
    }

    private static class TestDataGenerator {
        private static final String[] LOREM = "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nunc tempus cursus diam ac blandit. Ut ultrices lacus et mattis laoreet. Morbi vehicula tincidunt eros lobortis varius. Nam quis tortor commodo, vehicula ante vitae, sagittis enim. Vivamus mollis placerat leo non pellentesque. Nam blandit, odio quis facilisis posuere, mauris elit tincidunt ante, ut eleifend augue neque dictum diam. Curabitur sed lacus eget dolor laoreet cursus ut cursus elit. Phasellus quis interdum lorem, eget efficitur enim. Curabitur commodo, est ut scelerisque aliquet, urna velit tincidunt massa, tristique varius mi neque et velit. In condimentum quis nisi et ultricies. Nunc posuere felis a velit dictum suscipit ac non nisl. Pellentesque eleifend, purus vel consequat facilisis, sapien lacus rutrum eros, quis finibus lacus magna eget est. Nullam eros nisl, sodales et luctus at, lobortis at sem.".split(" ");

        private int curWord = 0;

        List<String> getNext(int nWords) {
            List<String> words = new ArrayList<>();

            for (int i = 0; i < nWords; i++) {
                if (curWord == Integer.MAX_VALUE) {
                    curWord = 0;
                }

                words.add(LOREM[curWord % LOREM.length]);
                curWord++;
            }

            return words;
        }
    }
}
```


