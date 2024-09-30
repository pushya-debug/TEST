import streamlit as st
import pandas as pd

# App layout
st.title("Snowflake Data Viewer")
st.write("This app displays data from the Snowflake target table.")

# Establish a connection to Snowflake
cnx = st.connection("snowflake")
session = cnx.session()

# Query to get data from the target_table
def get_data():
    query = "SELECT * FROM target_table LIMIT 100;"
    return session.sql(query).collect()

# Button to fetch data
if st.button("Load Data"):
    data = get_data()
    # Convert to DataFrame for better visualization
    df = pd.DataFrame(data, columns=["LOG_FILE_NAME", "LOG_FILE_ROW_ID", "LOAD_LTZ", "DATETIME_ISO8601", "USER_EVENT", "USER_LOGIN", "IP_ADDRESS"])
    st.write(df)

# Close the connection when the app stops
if cnx:
    cnx.close()
