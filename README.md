import flet as ft



def main(page: ft.Page):
    page.title = "ALI project"
    page.vertical_alignment = ft.MainAxisAlignment.CENTER

    txt_number = ft.TextField(value="0", text_align=ft.TextAlign.RIGHT, width=100)

    def minus_click(e):
        if int(txt_number.value) > 0:
            txt_number.value = str(int(txt_number.value) - 1)
            page.update()


    def plus_click(e):
        txt_number.value = str(int(txt_number.value) + 1)
        page.update()

    def btn_click(e):
        if not txt_name.value:
            txt_name.error_text = "Please enter your name"
            page.update()
        else:
            name = txt_name.value
            page.clean()
            page.add(ft.Text(f"my name is {name} ,and my age is {color_dropdown.value} "))
    
    output_text = ft.Text()
    color_dropdown = ft.Dropdown(
    width=100,
    options=[
        ft.dropdown.Option("1-18"),
        ft.dropdown.Option("19-40"),
        ft.dropdown.Option("+ 41"),
    ],
    )

    page.add(color_dropdown, output_text)


    txt_name = ft.TextField(label="Your name")

    page.add(txt_name, ft.ElevatedButton("tap here to get answer !", on_click=btn_click))

    page.add(
        ft.Row(
            [
                ft.IconButton(ft.icons.REMOVE, on_click=minus_click),
                txt_number,
                ft.IconButton(ft.icons.ADD, on_click=plus_click),
            ],
            alignment=ft.MainAxisAlignment.CENTER,
        )
    )

ft.app(main)
