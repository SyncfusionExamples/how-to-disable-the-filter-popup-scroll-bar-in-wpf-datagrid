# How to disable the FilterPopup Scrollbar in WPF DataGrid?

## About the sample
This example illustrates how to disable the FilterPopup Scrollbar in WPF DataGrid

By default, [WPF DataGrid](https://www.syncfusion.com/wpf-ui-controls/datagrid) (SfDataGrid) does not provide the direct support to disable the Scrollbar at FilterPopup in [CheckboxFilterControl](https://help.syncfusion.com/cr/wpf/Syncfusion.UI.Xaml.Grid.CheckboxFilterControl.html). You can disable the Scrollbar at FilterPopup by overriding the [CheckboxFilterControl](https://help.syncfusion.com/cr/wpf/Syncfusion.UI.Xaml.Grid.CheckboxFilterControl.html) Template and change the **HorizontalScrollBarVisibility** and **VerticalScrollBarVisibility** property as **Hidden** or **Disabled** in **ScrollViewer** of **PART_ItemsControl** Template in [SfDataGrid](https://help.syncfusion.com/cr/wpf/Syncfusion.UI.Xaml.Grid.SfDataGrid.html). 

```XML

 <Window.Resources>

        <syncfusion:VisiblityConverter x:Key="VisiblityConverter" />
        <syncfusion:BoolToVisiblityConverter x:Key="boolToVisiblityConverter" />
        <syncfusion:TextVisibilityConverter x:Key="textBlockVisibilityConverter" />
        <syncfusion:ReverseVisibilityConverter x:Key="reverseVisibilityConverter" />
        <syncfusion:LoadingVisiblityConverter x:Key="loadingVisiblityConverter" />
        <syncfusion:ListItemsVisiblityConverter x:Key="listItemsVisiblityConverter" />
        <syncfusion:HeightToMarginConverter x:Key="heightToMarginConverter" />
        <syncfusion:ResourceNameConverter x:Key="resourceNameConverter" />
        <syncfusion:AdvancedFiltersButtonVisibiltyConverter x:Key="advancedFilterButtonVisibilityConverter" />
        <syncfusion:FilteredFromCheckVisibilityConverter x:Key="filteredFromCheckVisibilityConverter" />

        <DataTemplate x:Key="CheckboxFilterControlItemTemplate">
            <CheckBox Margin="4"
            HorizontalAlignment="Stretch"
            HorizontalContentAlignment="Stretch"
            Content="{Binding DisplayText,
                            Mode=OneWay}"
            Focusable="False"
            FontFamily="{Binding FontFamily,RelativeSource={RelativeSource Self}}"
            FontSize="{Binding FontSize,RelativeSource={RelativeSource Self}}"
            FontStretch="{Binding FontStretch,RelativeSource={RelativeSource Self}}"
            FontStyle="{Binding FontStyle,RelativeSource={RelativeSource Self}}"
            FontWeight="{Binding FontWeight,RelativeSource={RelativeSource Self}}"
            Foreground="{Binding Foreground,RelativeSource={RelativeSource Self}}"
            IsChecked="{Binding IsSelected,
                                Mode=TwoWay}" />
        </DataTemplate>

        <Style x:Key="deleteBtnStyle" TargetType="{x:Type Button}">
            <Setter Property="Template">
                <Setter.Value>
                    <ControlTemplate TargetType="{x:Type Button}">
                        <Border x:Name="PART_DeleteButtonPresenter"
                            HorizontalAlignment="Stretch"
                            VerticalAlignment="Stretch"
                            BorderBrush="Black">
                            <Border.Background>
                                <LinearGradientBrush StartPoint="0.5,0" EndPoint="0.5,1">
                                    <GradientStop Offset="0.036" Color="#FFF6F7F8" />
                                    <GradientStop Offset="0.901" Color="#FFDEE2E9" />
                                </LinearGradientBrush>
                            </Border.Background>
                            <VisualStateManager.VisualStateGroups>
                                <VisualStateGroup x:Name="CommonStates">
                                    <VisualState x:Name="Normal">
                                        <Storyboard>
                                            <ColorAnimationUsingKeyFrames Storyboard.TargetName="PART_DeleteButtonPath" Storyboard.TargetProperty="(Shape.Fill).(SolidColorBrush.Color)">
                                                <EasingColorKeyFrame KeyTime="0" Value="#FF777777" />
                                            </ColorAnimationUsingKeyFrames>
                                            <ColorAnimationUsingKeyFrames Storyboard.TargetName="PART_DeleteButtonPresenter" Storyboard.TargetProperty="(Border.BorderBrush).(SolidColorBrush.Color)">
                                                <EasingColorKeyFrame KeyTime="0" Value="#FFABABAB" />
                                            </ColorAnimationUsingKeyFrames>
                                            <ThicknessAnimationUsingKeyFrames Storyboard.TargetName="PART_DeleteButtonPresenter" Storyboard.TargetProperty="(Border.BorderThickness)">
                                                <EasingThicknessKeyFrame KeyTime="0" Value="1" />
                                            </ThicknessAnimationUsingKeyFrames>
                                        </Storyboard>
                                    </VisualState>
                                    <VisualState x:Name="MouseOver">
                                        <Storyboard>
                                            <ColorAnimationUsingKeyFrames Storyboard.TargetName="PART_DeleteButtonPath" Storyboard.TargetProperty="(Shape.Fill).(SolidColorBrush.Color)">
                                                <EasingColorKeyFrame KeyTime="0" Value="#FF777777" />
                                            </ColorAnimationUsingKeyFrames>
                                            <ColorAnimationUsingKeyFrames Storyboard.TargetName="PART_DeleteButtonPresenter" Storyboard.TargetProperty="(Border.BorderBrush).(SolidColorBrush.Color)">
                                                <EasingColorKeyFrame KeyTime="0" Value="#FFABABAB" />
                                            </ColorAnimationUsingKeyFrames>
                                            <ThicknessAnimationUsingKeyFrames Storyboard.TargetName="PART_DeleteButtonPresenter" Storyboard.TargetProperty="(Border.BorderThickness)">
                                                <EasingThicknessKeyFrame KeyTime="0" Value="1" />
                                            </ThicknessAnimationUsingKeyFrames>
                                        </Storyboard>
                                    </VisualState>
                                    <VisualState x:Name="Pressed">
                                        <Storyboard>
                                            <ColorAnimationUsingKeyFrames Storyboard.TargetName="PART_DeleteButtonPath" Storyboard.TargetProperty="(Shape.Fill).(SolidColorBrush.Color)">
                                                <EasingColorKeyFrame KeyTime="0" Value="#FF777777" />
                                            </ColorAnimationUsingKeyFrames>
                                            <ColorAnimationUsingKeyFrames Storyboard.TargetName="PART_DeleteButtonPresenter" Storyboard.TargetProperty="(Border.BorderBrush).(SolidColorBrush.Color)">
                                                <EasingColorKeyFrame KeyTime="0" Value="#FFABABAB" />
                                            </ColorAnimationUsingKeyFrames>
                                            <ThicknessAnimationUsingKeyFrames Storyboard.TargetName="PART_DeleteButtonPresenter" Storyboard.TargetProperty="(Border.BorderThickness)">
                                                <EasingThicknessKeyFrame KeyTime="0" Value="1" />
                                            </ThicknessAnimationUsingKeyFrames>
                                        </Storyboard>
                                    </VisualState>
                                    <VisualState x:Name="Disabled" />
                                </VisualStateGroup>
                            </VisualStateManager.VisualStateGroups>
                            <Path x:Name="PART_DeleteButtonPath"
                              Margin="3"
                              Data="F1M54.0573,47.8776L38.1771,31.9974 54.0547,16.1198C55.7604,14.4141 55.7604,11.6511 54.0573,9.94531 52.3516,8.23962 49.5859,8.23962 47.8802,9.94531L32.0026,25.8229 16.1224,9.94531C14.4167,8.23962 11.6511,8.23962 9.94794,9.94531 8.24219,11.6511 8.24219,14.4141 9.94794,16.1198L25.8255,32 9.94794,47.8776C8.24219,49.5834 8.24219,52.3477 9.94794,54.0534 11.6511,55.7572 14.4167,55.7585 16.1224,54.0534L32.0026,38.1745 47.8802,54.0534C49.5859,55.7585 52.3516,55.7572 54.0573,54.0534 55.7604,52.3477 55.763,49.5834 54.0573,47.8776z"
                              Fill="Gray"
                              Stretch="Uniform">
                                <Path.RenderTransform>
                                    <TransformGroup>
                                        <RotateTransform Angle="0" />
                                        <ScaleTransform ScaleX="1" ScaleY="1" />
                                    </TransformGroup>
                                </Path.RenderTransform>
                            </Path>
                        </Border>
                        <ControlTemplate.Triggers>
                            <Trigger Property="IsFocused" Value="True" />
                            <Trigger Property="IsDefaulted" Value="True" />
                            <Trigger Property="IsMouseOver" Value="True" />
                            <Trigger Property="IsPressed" Value="True" />
                            <Trigger Property="IsEnabled" Value="False" />
                        </ControlTemplate.Triggers>
                    </ControlTemplate>
                </Setter.Value>
            </Setter>
        </Style>

   <Style  TargetType="syncfusion:CheckboxFilterControl">
            <Setter Property="ItemTemplate" Value="{StaticResource CheckboxFilterControlItemTemplate}"/>
            <Setter Property="Template">
                <Setter.Value>
                    <ControlTemplate TargetType="syncfusion:CheckboxFilterControl">
                        <Grid Height="{TemplateBinding Height}">
                            <Grid.ColumnDefinitions>
                                <ColumnDefinition Width="30" />
                                <ColumnDefinition Width="*" />
                            </Grid.ColumnDefinitions>

                            <Border Grid.Column="0"
                                Width="19"
                                Height="19"
                                Margin="4,39,4,4"
                                VerticalAlignment="Top"
                                BorderBrush="#FFB2B2B2"
                                BorderThickness="1,1,1,1"
                                Visibility="{Binding FilteredFrom,
                                                     RelativeSource={RelativeSource FindAncestor,
                                                                                    AncestorType={x:Type syncfusion:GridFilterControl}},
                                                     Converter={StaticResource filteredFromCheckVisibilityConverter}}">
                                <Path x:Name="PART_FilteredFromCheck1"
                                  Width="15"
                                  Height="15"
                                  Data="M 12.4227,0.00012207C 12.4867,0.126587 12.5333,0.274536 12.6787,0.321411C 9.49199,3.24792 6.704,6.57336 4.69865,10.6827C 4.04399,11.08 3.47066,11.5573 2.83199,11.9706C 2.09467,10.2198 1.692,8.13196 3.8147e-006,7.33606C 0.500004,6.79871 1.31733,6.05994 1.93067,6.2428C 2.85999,6.51868 3.14,7.9054 3.60399,8.81604C 5.80133,5.5387 8.53734,2.19202 12.4227,0.00012207 Z "
                                  Fill="Gray"
                                  Stretch="Uniform"
                                  Visibility="{Binding FilteredFrom,
                                                       RelativeSource={RelativeSource FindAncestor,
                                                                                      AncestorType={x:Type syncfusion:GridFilterControl}},
                                                       Converter={StaticResource filteredFromCheckVisibilityConverter}}">
                                    <Path.RenderTransform>
                                        <TransformGroup>
                                            <TransformGroup.Children>
                                                <RotateTransform Angle="0" />
                                                <ScaleTransform ScaleX="1" ScaleY="1" />
                                            </TransformGroup.Children>
                                        </TransformGroup>
                                    </Path.RenderTransform>
                                </Path>
                            </Border>

                            <Grid Grid.Column="1">
                                <Grid.RowDefinitions>
                                    <RowDefinition Height="Auto" />
                                    <RowDefinition Height="*" />
                                </Grid.RowDefinitions>

                                <Grid Margin="0,8,4,2" Background="{TemplateBinding Background}" Visibility="{TemplateBinding SearchOptionVisibility}">

                                    <TextBox x:Name="PART_SearchTextBox"
                                         Height="25"
                                         HorizontalAlignment="Stretch"
                                         VerticalAlignment="Center"
                                         VerticalContentAlignment="Center"
                                         FontFamily="{TemplateBinding FontFamily}"
                                         FontSize="{TemplateBinding FontSize}"
                                         FontStretch="{TemplateBinding FontWeight}"
                                         FontStyle="{TemplateBinding FontStyle}"
                                         FontWeight="{TemplateBinding FontWeight}"
                                         BorderBrush="#FF727272"
                                         BorderThickness="1" />

                                    <TextBlock Margin="5,0,0,0"
                                           HorizontalAlignment="Left"
                                           VerticalAlignment="Center"
                                           Foreground="{TemplateBinding Foreground}"
                                           FontFamily="{TemplateBinding FontFamily}"
                                           FontSize="{TemplateBinding FontSize}"
                                           FontStretch="{TemplateBinding FontWeight}"
                                           FontStyle="{TemplateBinding FontStyle}"
                                           FontWeight="{TemplateBinding FontWeight}"
                                           IsHitTestVisible="False"
                                           Opacity="0.7"
                                           Text="{Binding Source={x:Static Member=syncfusion:GridResourceWrapper.Search}}"
                                           Visibility="{TemplateBinding SearchTextBlockVisibility}" />

                                    <Border Width="18"
                                        Height="18"
                                        Margin="0,0,5,0"
                                        HorizontalAlignment="Right"
                                        Visibility="{Binding Text,
                                                             ElementName=PART_SearchTextBox,
                                                             ConverterParameter=searchIcon,
                                                             Converter={StaticResource textBlockVisibilityConverter}}">
                                        <Path Data="F1M-185.925,-2026.96L-203.062,-2048.74C-197.485,-2056.51 -197.433,-2067.31 -203.64,-2075.2 -211.167,-2084.76 -225.019,-2086.42 -234.588,-2078.89 -244.154,-2071.36 -245.808,-2057.51 -238.282,-2047.94 -231.986,-2039.95 -221.274,-2037.5 -212.337,-2041.31L-195.262,-2019.61 -185.925,-2026.96z M-231.201,-2053.51C-235.653,-2059.17 -234.674,-2067.36 -229.02,-2071.81 -223.36,-2076.26 -215.169,-2075.29 -210.721,-2069.63 -206.269,-2063.97 -207.245,-2055.78 -212.902,-2051.33 -218.559,-2046.88 -226.752,-2047.86 -231.201,-2053.51z"
                                          Fill="Gray"
                                          RenderTransformOrigin="0.5,0.5"
                                          Stretch="Uniform">
                                            <Path.RenderTransform>
                                                <TransformGroup>
                                                    <RotateTransform Angle="0" />
                                                    <ScaleTransform ScaleX="1" ScaleY="1" />
                                                </TransformGroup>
                                            </Path.RenderTransform>
                                        </Path>
                                    </Border>
                                    <Button x:Name="PART_DeleteButton"
                                        Width="25"
                                        Height="25"
                                        HorizontalAlignment="Right"
                                        VerticalAlignment="Stretch"
                                        Style="{StaticResource deleteBtnStyle}"
                                        FontFamily="{TemplateBinding FontFamily}"
                                        FontSize="{TemplateBinding FontSize}"
                                        FontStretch="{TemplateBinding FontWeight}"
                                        FontStyle="{TemplateBinding FontStyle}"
                                        FontWeight="{TemplateBinding FontWeight}"
                                        Visibility="{Binding Text,
                                                             ElementName=PART_SearchTextBox,
                                                             ConverterParameter=deletebtn,
                                                             Converter={StaticResource textBlockVisibilityConverter}}" />
                                </Grid>
                                <Border Grid.Row="1"
                                    Margin="0,4,4,4"
                                    BorderBrush="#FFC0C0C0"
                                    BorderThickness="1">
                                    <Grid>
                                        <TextBlock Margin="0,25,0,0"
                                               HorizontalAlignment="Center"
                                               VerticalAlignment="Top"
                                               FontFamily="{TemplateBinding FontFamily}"
                                               FontSize="{TemplateBinding FontSize}"
                                               FontStretch="{TemplateBinding FontWeight}"
                                               FontStyle="{TemplateBinding FontStyle}"
                                               FontWeight="{TemplateBinding FontWeight}"
                                               Text="{Binding Source={x:Static Member=syncfusion:GridResourceWrapper.NoItems}}"
                                               Visibility="{Binding HasItemsSource,
                                                                    RelativeSource={RelativeSource TemplatedParent},
                                                                    Converter={StaticResource ResourceKey=reverseVisibilityConverter}}" />
                                        <Grid Visibility="{Binding HasItemsSource, RelativeSource={RelativeSource TemplatedParent}, Converter={StaticResource ResourceKey=boolToVisiblityConverter}}">
                                            <Grid.RowDefinitions>
                                                <RowDefinition Height="Auto" />
                                                <RowDefinition Height="*" />
                                            </Grid.RowDefinitions>
                                            <Grid Grid.Row="1">
                                                <Grid.Resources>
                                                    <Storyboard x:Key="LaoadingAnimation" RepeatBehavior="Forever">
                                                        <DoubleAnimationUsingKeyFrames Storyboard.TargetName="Path" Storyboard.TargetProperty="(UIElement.RenderTransform).(TransformGroup.Children)[2].(RotateTransform.Angle)">
                                                            <EasingDoubleKeyFrame KeyTime="0" Value="0" />
                                                            <EasingDoubleKeyFrame KeyTime="0:0:5" Value="1170" />
                                                        </DoubleAnimationUsingKeyFrames>
                                                    </Storyboard>
                                                </Grid.Resources>
                                                <Path x:Name="Path"
                                                  Width="26"
                                                  Height="26"
                                                  Data="M33.091251,58.314999C35.398258,58.314999 37.268002,60.186188 37.268002,62.490997 37.268002,64.797111 35.398258,66.667 33.091251,66.667 30.786645,66.667 28.917001,64.797111 28.917001,62.490997 28.917001,60.186188 30.786645,58.314999 33.091251,58.314999z M47.2943,55.271999C49.601437,55.271999 51.471003,57.141811 51.471003,59.447948 51.471003,61.752788 49.601437,63.624 47.2943,63.624 44.989765,63.624 43.119999,61.752788 43.119999,59.447948 43.119999,57.141811 44.989765,55.271999 47.2943,55.271999z M18.6666,54.257999C21.252921,54.257999 23.352,56.354423 23.352,58.94035 23.352,61.526379 21.252921,63.624 18.6666,63.624 16.08058,63.624 13.984001,61.526379 13.984001,58.94035 13.984001,56.354423 16.08058,54.257999 18.6666,54.257999z M57.4405,45.199001C59.3416,45.199001 60.891001,46.743435 60.891001,48.651199 60.891001,50.557564 59.3416,52.102001 57.4405,52.102001 55.534201,52.102001 53.99,50.557564 53.99,48.651199 53.99,46.743435 55.534201,45.199001 57.4405,45.199001z M8.3045502,43.967003C10.890694,43.967003 12.987,46.064644 12.987,48.6507 12.987,51.236656 10.890694,53.333 8.3045502,53.333 5.7185383,53.333 3.6219997,51.236656 3.6219997,48.6507 3.6219997,46.064644 5.7185383,43.967003 8.3045502,43.967003z M61.643499,30.851999C63.544542,30.851999 65.093996,32.396133 65.093996,34.30365 65.093996,36.209869 63.544542,37.754002 61.643499,37.754002 59.737253,37.754002 58.193001,36.209869 58.193001,34.30365 58.193001,32.396133 59.737253,30.851999 61.643499,30.851999z M4.6824703,29.619999C7.268652,29.619999 9.3649998,31.717722 9.3649998,34.30365 9.3649998,36.88958 7.268652,38.986 4.6824703,38.986 2.0965385,38.986 0,36.88958 0,34.30365 0,31.717722 2.0965385,29.619999 4.6824703,29.619999z M57.440451,16.938999C59.101923,16.938999 60.455999,18.287865 60.455999,19.9543 60.455999,21.620834 59.101923,22.971001 57.440451,22.971001 55.773779,22.971001 54.425001,21.620834 54.425001,19.9543 54.425001,18.287865 55.773779,16.938999 57.440451,16.938999z M8.3045502,15.272C10.890694,15.272 12.987,17.368345 12.987,19.9543 12.987,22.540255 10.890694,24.637999 8.3045502,24.637999 5.7185383,24.637999 3.6219997,22.540255 3.6219997,19.9543 3.6219997,17.368345 5.7185383,15.272 8.3045502,15.272z M47.294703,7.0829992C48.875502,7.0829996 50.167002,8.3696136 50.167002,9.9543542 50.167002,11.540385 48.875502,12.827 47.294703,12.827 45.711302,12.827 44.425001,11.540385 44.425001,9.9543542 44.425001,8.3696136 45.711302,7.0829996 47.294703,7.0829992z M18.666401,4.0399989C21.61159,4.0399999 23.997,6.4307284 23.997001,9.3748798 23.997,12.319001 21.61159,14.710999 18.666401,14.710999 15.72391,14.710999 13.336,12.319001 13.335999,9.3748798 13.336,6.4307284 15.72391,4.0399999 18.666401,4.0399989z M33.091201,0C36.294464,-7.5211233E-08 38.891,2.59503 38.891,5.7968797 38.891,8.9987201 36.294464,11.595 33.091201,11.595 29.890533,11.595 27.294,8.9987201 27.294001,5.7968797 27.294,2.59503 29.890533,-7.5211233E-08 33.091201,0z"
                                                  Fill="Gray"
                                                  RenderTransformOrigin="0.5,0.5"
                                                  Stretch="Uniform"
                                                  Visibility="{Binding IsItemSourceLoaded,
                                                                       Mode=TwoWay,
                                                                       RelativeSource={RelativeSource TemplatedParent},
                                                                       ConverterParameter={StaticResource LaoadingAnimation},
                                                                       Converter={StaticResource ResourceKey=loadingVisiblityConverter}}">
                                                    <Path.RenderTransform>
                                                        <TransformGroup>
                                                            <ScaleTransform />
                                                            <SkewTransform />
                                                            <RotateTransform />
                                                            <TranslateTransform />
                                                        </TransformGroup>
                                                    </Path.RenderTransform>
                                                </Path>

                                                <ItemsControl x:Name="PART_ItemsControl"
                                                          Height="{TemplateBinding Height}"
                                                          HorizontalAlignment="Stretch"
                                                          VerticalAlignment="Stretch"
                                                          HorizontalContentAlignment="Stretch"
                                                          VerticalContentAlignment="Stretch"
                                                          ItemTemplate="{TemplateBinding ItemTemplate}"
                                                          ItemsSource="{TemplateBinding ItemsSource}"
                                                          KeyboardNavigation.TabNavigation="Continue"
                                                          Visibility="{Binding IsItemSourceLoaded,
                                                                               RelativeSource={RelativeSource TemplatedParent},
                                                                               Converter={StaticResource ResourceKey=boolToVisiblityConverter}}">
                                                    <ItemsControl.Template>
                                                        <ControlTemplate TargetType="{x:Type ItemsControl}">
                                                            <Border Background="{TemplateBinding Background}"
                                                                BorderBrush="{TemplateBinding BorderBrush}"
                                                                Padding="{TemplateBinding Padding}">
                                                                <Grid>
                                                                    <ScrollViewer HorizontalAlignment="Stretch"
                                                                              CanContentScroll="True"
                                                                              HorizontalScrollBarVisibility="Hidden"
                                                                              Padding="2"
                                                                              SnapsToDevicePixels="true"
                                                                              VerticalScrollBarVisibility="Disabled">
                                                                        <ItemsPresenter x:Name="PART_ItemsPresenter"
                                                                                    Margin="{Binding ActualHeight,
                                                                          ElementName=PART_CheckBox, UpdateSourceTrigger=PropertyChanged,
                                                                                                     Converter={StaticResource heightToMarginConverter}}"
                                                                                    ClipToBounds="True"
                                                                                    Focusable="False" />
                                                                    </ScrollViewer>
                                                                    <TextBlock Margin="{Binding ElementName=PART_ItemsPresenter,
                                                                                            Path=Margin}"
                                                                           HorizontalAlignment="Center"
                                                                           VerticalAlignment="Top"
                                                                           Foreground="{TemplateBinding Foreground}"
                                                                           Text="{Binding Source={x:Static Member=syncfusion:GridResourceWrapper.NoMatches}}"
                                                                           Visibility="{Binding ItemsSource,
                                                                                                RelativeSource={RelativeSource TemplatedParent},
                                                                                                ConverterParameter=NoMatchText,
                                                                                                Converter={StaticResource ResourceKey=listItemsVisiblityConverter}}" />
                                                                </Grid>
                                                            </Border>
                                                        </ControlTemplate>
                                                    </ItemsControl.Template>
                                                    <ItemsControl.ItemsPanel>
                                                        <ItemsPanelTemplate>
                                                            <VirtualizingStackPanel HorizontalAlignment="Stretch" />
                                                        </ItemsPanelTemplate>
                                                    </ItemsControl.ItemsPanel>

                                                </ItemsControl>
                                            </Grid>
                                            <Border Grid.Row="1"
                                                Margin="0,0,20,0"
                                                VerticalAlignment="Top"
                                                Background="{TemplateBinding Background}"
                                                Visibility="{Binding ItemsSource,
                                                                     ElementName=PART_ItemsControl,
                                                                     ConverterParameter=ItemsControl,
                                                                     Converter={StaticResource ResourceKey=listItemsVisiblityConverter}}">
                                                <CheckBox x:Name="PART_CheckBox"
                                                      Margin="10,10,4,4"
                                                      HorizontalAlignment="Stretch"
                                                      VerticalAlignment="Center"
                                                      Content="{Binding Source={x:Static Member=syncfusion:GridResourceWrapper.SelectAll}}"
                                                      Focusable="False"
                                                      FontFamily="{TemplateBinding FontFamily}"
                                                      FontSize="{TemplateBinding FontSize}"
                                                      FontStretch="{TemplateBinding FontWeight}"
                                                      FontStyle="{TemplateBinding FontStyle}"
                                                      FontWeight="{TemplateBinding FontWeight}"
                                                      Foreground="{TemplateBinding Foreground}"
                                                      IsThreeState="True"
                                                      Visibility="{Binding Visibility,
                                                                           ElementName=PART_ItemsControl}" />
                                            </Border>
                                        </Grid>

                                    </Grid>
                                </Border>
                            </Grid>
                        </Grid>
                    </ControlTemplate>
                </Setter.Value>
            </Setter>
        </Style>
</Window.Resources>

```

![Shows the disabled the Scrollbar at FilterPopup in SfDataGrid](DisabletheScrollbar.gif)

Take a moment to peruse the [WPF DataGrid - Filtering documentation](https://help.syncfusion.com/wpf/datagrid/filtering), where you can find about Filtering with code examples.

Please refer this [link](https://www.syncfusion.com/wpf-ui-controls/datagrid) to know about the essential features of WPF DataGrid.

KB article - [How to disable the FilterPopup Scrollbar in WPF DataGrid?](https://www.syncfusion.com/kb/12377/how-to-disable-the-filterpopup-scrollbar-in-wpf-datagrid-sfdatagrid)

## Requirements to run the demo
Visual Studio 2015 and above versions
